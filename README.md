# Phoenix with docker lab

This is a demo project that includes:
- Deployment with ansistrano in a separate docker container
- Nginx example
- Configuration management with conform
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
