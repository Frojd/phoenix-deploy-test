# Phoenix with docker lab

This is a example project that includes:
- Phoenix and Elixir with Postgres
- Configuration management with conform
- Deployment with destillery and ansistrano (through a separate docker container)
- Nginx example
- Circle 2.0 build example
- Migrations

## Clean install

1. Copy configuration

```
cp docker/config/web.example.env docker/config/web.env
cp docker/config/db.example.env docker/config/db.env
```

2. Run: docker-compose up
3. Done. Visit localhost:4000


## Tests

- `docker-compose run --rm web test`


## Local deployment with ansistrano

Building release:

```
docker-compose exec web bash -c "MIX_ENV=prod mix release --env=prod"
```

Deploying to local webserver:

```
dc run --rm deploy ansible-playbook deploy.yml -i stages/local
```


## TODO

- [ ] Extend config value list (with log destination among others)
- [ ] Extend env list to include cookie signage
- [ ] Look into asset bundling
- [ ] Investigate CI builds
- [ ] Research best approach for media handling


