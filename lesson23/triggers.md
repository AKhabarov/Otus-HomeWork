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

        RETURN NULL;

    END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER t_sales_summary
AFTER INSERT OR UPDATE OR DELETE ON sales
    FOR EACH ROW EXECUTE FUNCTION sales_summary();
```

### Проверка работы триггера:

1. insert
   
![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/497f0dd5-6b0c-43f1-9b0a-5ae81581ebb1)

2. delete

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/053b258c-2932-415b-8ae6-0dd317fb71ec)

3. update

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/d8d3f014-1f8e-4973-b466-d8d5af300f78)

