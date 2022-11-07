# timeseries_data_db_comparison


- env : Linux Ubuntu 18.04 LTS
- characteristics of input data: more than number of 2100 columns
- SQL compile setting change to enable columns: 32767

```
> wc -l input_data.csv 
2109
````


1. Time-series data on SQLite

Compile SQLite (https://www.sqlite.org/cli.html)

```
wget https://www.sqlite.org/2022/sqlite-autoconf-3390400.tar.gz
gunzip sqlite-autoconf-3390400.tar.gz 
tar -xvf sqlite-autoconf-3390400.tar 
cd sqlite-autoconf-3390400/
sh configure
make sqlite3.pc 
make sqlite3.c
make sqlite3.c
make
sl

gcc -Os -I. -DSQLITE_THREADSAFE=0\
-DSQLITE_ENABLE_FTS4  \
-DSQLITE_ENABLE_FTS5\
-DSQLITE_ENABLE_JSON1\
-DSQLITE_ENABLE_RTREE \
-DSQLITE_ENABLE_EXPLAIN_COMMENTS   \
-DHAVE_USLEEP\
-DHAVE_READLINE \
-DSQLITE_MAX_COLUMN=32767 \
-DSQLITE_MAX_SQL_LENGTH=1073741824 \
-DSQLITE_MAX_LENGTH=1273741824  \
shell.c sqlite3.c -ldl -lm -lreadline -lncurses -o sqlite3

```





