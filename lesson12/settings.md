* развернуть виртуальную машину любым удобным способом
* поставить на неё PostgreSQL 15 любым способом

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/3d270905-6085-4e78-b246-33a74379b351)

* до изменения настроек, tps=522:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/82bc219a-78f2-426d-86b5-f061273e21f7)

* Настройки (https://pgconfigurator.cybertec.at/):

# Connectivity
max_connections = 20
superuser_reserved_connections = 3

# Memory Settings
shared_buffers = '1024 MB'
work_mem = '32 MB'
maintenance_work_mem = '320 MB'
huge_pages = off
effective_cache_size = '3 GB'
effective_io_concurrency = 100 # concurrent IO only really activated if OS supports posix_fadvise function
random_page_cost = 1.25 # speed of random disk access relative to sequential access (1.0)

# Monitoring
shared_preload_libraries = 'pg_stat_statements' # per statement resource usage stats
track_io_timing=on # measure exact block IO times
track_functions=pl # track execution times of pl-language procedures if any

# Replication
wal_level = replica # consider using at least 'replica'
max_wal_senders = 0
synchronous_commit = off

# Checkpointing:
checkpoint_timeout = '15 min'
checkpoint_completion_target = 0.9
max_wal_size = '1024 MB'
min_wal_size = '512 MB'


# WAL writing
wal_compression = on
wal_buffers = -1 # auto-tuned by Postgres till maximum of segment size (16MB by default)


# Background writer
bgwriter_delay = 200ms
bgwriter_lru_maxpages = 100
bgwriter_lru_multiplier = 2.0
bgwriter_flush_after = 0

# Parallel queries:
max_worker_processes = 4
max_parallel_workers_per_gather = 2
max_parallel_maintenance_workers = 2
max_parallel_workers = 4
parallel_leader_participation = on

# Advanced features
enable_partitionwise_join = on
enable_partitionwise_aggregate = on
jit = on
max_slot_wal_keep_size = '1000 MB'
track_wal_io_timing = on
maintenance_io_concurrency = 100
wal_recycle = on

* тест после применения настроек synchronous_commit = off, tps = 4779:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/9648fe5b-bb56-4ca4-84ea-fac91eb701cb)

* тест с теми же настройками, synchronous_commit = on, tps = 562:

![image](https://github.com/AKhabarov/Otus-HomeWork/assets/40095258/e86289c1-8959-4865-a5ab-20c607e8472f)

*Вывод: значительный прирост производительности дает настройка synchronous_commit = off, но ее следует применять только в базах где не страшно потерять часть транзакций при аварии.*
