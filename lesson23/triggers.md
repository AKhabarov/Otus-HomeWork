# Триггеры
## Создать триггер на таблице продаж, для поддержки данных в витрине в актуальном состоянии (вычисляющий при каждой продаже сумму и записывающий её в витрину)

### Первоначальное заполнение БД, отчет о продажах:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/b0e764d1-6eab-4ece-8661-69003cc87266)

### создаем витрину:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/5731897b-7740-4769-a01d-bf2d1d04363f)

### Триггерная функция и триггер:

```
CREATE OR REPLACE FUNCTION sales_summary() RETURNS TRIGGER
AS $$
    DECLARE
        delta_good_id          integer;
        delta_sales_qty        integer;
        delta_name varchar(63);
        delta_sum numeric(16,2);
      
     BEGIN

        -- Вычислить изменение количества/суммы.
        IF (TG_OP = 'DELETE') THEN

            delta_good_id = OLD.good_id;
            delta_sales_qty = -1 * OLD.sales_qty;
        
        ELSIF (TG_OP = 'UPDATE') THEN

            delta_good_id = OLD.good_id;
            delta_sales_qty = NEW.sales_qty - OLD.sales_qty;

        ELSIF (TG_OP = 'INSERT') THEN

            delta_good_id = NEW.good_id;
            delta_sales_qty = NEW.sales_qty;

        END IF;
        
        SELECT good_name,good_price*delta_sales_qty INTO delta_name,delta_sum FROM goods WHERE goods_id=delta_good_id;

        -- Внести новые значения в существующую строку итогов или
        -- добавить новую.
        <<insert_update>>
        LOOP
            UPDATE good_sum_mart
                SET sum_sale = sum_sale + delta_sum
                WHERE good_name = delta_name;

            EXIT insert_update WHEN found;

            BEGIN
                INSERT INTO good_sum_mart (
                            good_name,
                            sum_sale)
                    VALUES (
                            delta_name,
                            delta_sum
                           );

                EXIT insert_update;

            EXCEPTION
                WHEN UNIQUE_VIOLATION THEN
                    -- ничего не делать
            END;
        END LOOP insert_update;

        RETURN NULL;```

    END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER t_sales_summary
AFTER INSERT OR UPDATE OR DELETE ON sales
    FOR EACH ROW EXECUTE FUNCTION sales_summary();
