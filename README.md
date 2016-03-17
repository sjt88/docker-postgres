## PostgreSQL Dockerfile

This is a fork of the official PostgreSQL Dockerfile. The primary addition being the retrieval and restoration of a dump (compressed with bzip2).

### Usage
Check out the official PostgreSQL docker image env variables and how to use this dockerfile here: https://hub.docker.com/_/postgres/

In addition to these the following is available:
```
DUMP_URL - direct URL to a the desired dump.bzip2 file
```

e.g:
```
docker build -t postgres_from_dump:1.0 .
docker run --name my-postgres-from-dump -e DUMP_URL=https://www.fuzzwork.co.uk/dump/postgres-latest.dmp.bz2 -e POSTGRES_PASSWORD=strongestpassword -e POSTGRES_DB=eve_static_dump -d postgres_from_dump:1.0
```
Will restore the latest eve online static dump from fuzzwork.co.uk to a database named eve_static_dump with user postgres (who is given the password "strongestpassword".
Once the dump is restored Postgres will be available on port 5432
