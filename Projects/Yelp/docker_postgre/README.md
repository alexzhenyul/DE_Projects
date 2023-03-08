## Docker - Postgre 
Use Docker to set up Postgre Database and PGAMDIN for Local Ingestio for the YELP dataset in JSON format 

Downloading the data

```bash
wget https://yelp-dataset.s3.amazonaws.com/YDC22/yelp_dataset.tgz?AWSAccessKeyId=AKIAJ3CYHOIAD6T2PGKA&Signature=oIxPAtaKM6Y2hhQ%2F9Mwyp%2FRlVA8%3D&Expires=1678273296
```
## Yelp dataset: 9.3GB  
- yelp_academic_dataset_business.json
- yelp_academic_dataset_checkin.json
- yelp_academic_dataset_review.json
- yelp_academic_dataset_tip.json
- yelp_academic_dataset_user.json

## Running Postgre with Docker

Linux/MacOS
 ```bash
docker run -it \
  -e POSTGRES_USER="yelp_root" \
  -e POSTGRES_PASSWORD="yelp_password" \
  -e POSTGRES_DB="yelp_db" \
  -v $(pwd)/yelp_postgres_data:/var/lib/postgresql/data \
  -p 5432:5432 \
  postgres:13
```

## CLI for Postgre

Install pgcli
```bash
pip install pgcli
```

Use pgcli to connect with postgre
```bash
pgcli -h localhost -p 5432 -u yelp_root -d yelp_db
```

## pgAdmin
Running pgAdmin via docker
```bash
docker run -it \
  -e PGADMIN_DEFAULT_EMAIL="admin@yelp.com" \
  -e PGADMIN_DEFAULT_PASSWORD="yelp_password" \
  -p 8080:80 \
  dpage/pgadmin4
```

## Postgre & pgAdmin Communication
Create network
```bash
docker network create pg-network-yelp
```

```bash
docker run -it \
  -e POSTGRES_USER="yelp_root" \
  -e POSTGRES_PASSWORD="yelp_password" \
  -e POSTGRES_DB="yelp_db" \
  -v $(pwd)/yelp_postgres_data:/var/lib/postgresql/data \
  -p 5432:5432 \
  --network=pg-network-yelp \
  --name pg-database \
  postgres:13
```

Run pgAdmin

```bash
docker run -it \
  -e PGADMIN_DEFAULT_EMAIL="admin@yelp.com" \
  -e PGADMIN_DEFAULT_PASSWORD="yelp_pasword" \
  -p 8080:80 \
  --network=pg-network-yelp \
  --name pgadmin \
  dpage/pgadmin4
```

# Docker-Compose
Run postgre.yaml file
```bash
docker-compose up
```

Run in detached mode:

```bash
docker-compose up -d
```

Shutting it down:

```bash
docker-compose down
```

## Ingestion Script for yelw dataset's 5 json file into Postgre
Take yelp_academic_dataset_business.json as exmaple, run the python script for data ingestion into postgre

```bash
json_file_name ="yelp_academic_dataset_business.json"

python ingest_data.py \
  --user=yelp_root \
  --password=yelp_password \
  --host=localhost \
  --port=5432 \
  --db=yelp_db \
  --table_name=yelp_business \
  --json_file_name=${json_file_name}
```