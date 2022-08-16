# Sentry setup docker-compose


#### Generate secret key

```bash
docker-compose run --rm sentry-base config generate-secret-key
```

And then set generated key to `SENTRY_SECRET_KEY` in `.env`.

#### Initialize database

If this is a new database, you'll need to run `upgrade`.

```bash
docker-compose run --rm sentry-base upgrade
```

And **create** an initial user, if you need.


### Service Start 

```bash
docker-compose up -d
```
