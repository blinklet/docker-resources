# Chinook

Builds Postgres DB with Chinook sample database

```bash
$ docker build \
    --tag postgres-chinook \
    --file Dockerfile .
```

Sample container:

```bash
$ docker run \
    --detach \
    --env POSTGRES_PASSWORD=abcd1234 \
    --network host \
    --name chinook1\
    postgres-chinook
```