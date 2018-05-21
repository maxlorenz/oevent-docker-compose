# Open Event v1 and v2 comparison using `docker-compose`

To have two instances of open event v1 and v2 running locally, one can use `docker-compose`. The installation instructions can be found [here](https://docs.docker.com/compose/install/#install-compose).

## Cloning the sites

In order to have the two projects running, execute `clone.sh` or copy the three clone commands from `clone.sh` into your terminal

## Starting the system

```bash
> docker-compose up
```

## Initializing the database

Two databases and users are created to allow for using one postgres image with both versions. See `postgres-initdb.d/create_db.sql` for details. To init both databases, run

```bash
docker-compose start
docker-compose run v1 python create_db.py && python manage.py db stamp head 
docker-compose run v2 python create_db.py && python manage.py db stamp head
```