# pg-schema-version

schema migration tool for postgres

inspired by flyway

flyway
========

http://flywaydb.org/getstarted/why.html

schema migrations can always be reverted easily — unless you have data

I vote for forward-only migrations, for rolling back we use our regular disaster recovery


tricks
=========

http://www.jeremyjarrell.com/using-flyway-db-with-distributed-version-control/

to avoid filename collisions across different branches
a migration starts with a utc timestamp
V20151006.174040.24034__some_migration.sql

migration starts with a letter V and description goes after two underscores


idempotend migrations
======================

sounds like a good idea,
but to me
on migration fail
the fail fast is a better strategy

to me a cleaner way look like this:
find out what failed,
fix the script, restore a test db from backup, try the migration again

http://thedailywtf.com/articles/Database-Changes-Done-Right


pgtap
=================

http://pgtap.org/

an easy way to install it

```
$ apt-get install postgresql-9.4-pgtap
$ psql -c "CREATE EXTENSION pgtap;"
```

in fact, pg_prove just passes everything off to prove --- http://stackoverflow.com/questions/16737631/run-pgtap-with-perl-prove-instead-of-pg-prove


so, we produce some tap test results
the prove command only understands lines without whitespaces
so we have to do this before tests
```
\pset format unaligned
```

misc
====================

TODO: handle file doesn't exist error 


