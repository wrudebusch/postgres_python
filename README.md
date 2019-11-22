William Rudebusch 
Aug 12, 2019

# Install Steps

Step 1: stop postgres if its running `sudo service postgresql stop`

## Docker
Step 2: install Docker and get the most recent postgres: `docker pull postgres`

Step 3: make new path for this comtainer: `make new dir for volumes: mkdir -p $HOME/docker/volumes/postgres`

Step 4: run the Docker image in one shot:
`docker run --rm   --name pg-docker -e POSTGRES_PASSWORD=docker -d -p 5432:5432 -v $HOME/docker/volumes/postgres:/var/lib/postgresql/data  postgres`

Step 5: log into postgres: `psql -h localhost -U postgres -d postgres`

Step 6: (testing, you can skip this) list databases 
`\l 
\q
`

Step 7: (testing, you can skip this) in a diff terminal connect to postgres and see that if its ok:
`psql -h localhost -p 5432 -U postgres -W  \l`

## Python

Step 9: innstall pandas, psycopg2, and sqlalchamey if you don't already have them
`python3 -m pip install --user pandas sqlalchemy psycopg2`

Step 10: run the script I wrote (note: it must be inthe same dir as the .csv files, which i am NOT including)
`python3 csv_to_postgres.py`

## SQL
Step 11: test to see if if worked:
`psql -h localhost -p 5432 -U postgres -W
\c postgres
\dt
`

## Docker cheatsheet
lists all containers: `sudo docker container ls`

kills a container: `sudo docker container kill [contianer_id]`

delete all stopped containers: `sudo docker container prune`
