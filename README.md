# Docker Datasources

This project aims to provide quick and easy steps for configuring database services so that you can start programming and testing as soon as possible.

## Notes

- The deployment instructions provided here are not suited for production use, please use them for testing and POCs only.
- On Linux, docker commands must be run as administrator.
- If you are deploying this on a hosting provider, you will need to use [Ngrok](Ngrok_example.md) to get a usable URL to connect to. If you use this locally, just remember to use `localhost`.


## General Requirements

- [Docker](https://docs.docker.com/engine/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Ngrok](https://ngrok.com/) (Optional)


## Service Setup

Navigate to the folder in which you want to store all the services present in this repository. Open a `cmd` and run the following command:

```bash
git clone https://github.com/danielcorrea28/quick-datasources-docker.git
```

Then, go to the section for the service you want to run and follow the specified steps.

### 🌿 MongoDB

1. Go to the MongoDB folder.

```bash
cd mongodb
```

2. Check the provided `docker-compose.yaml` [for MongoDB](./mongodb/docker-compose.yaml) and change _username_ and _password_ if it is necessary.

3. Run the deployment. 

```bash
docker-compose up -d
```
`Note: There is a version that uses a seed, in case you want to test with a DB with data`

```
docker-compose -f docker-compose.seeded.yaml up -d
```

`Note: If you did not make any configuration changes, use the following values.`

4. User:
`
develop_user
`

5. Password:
`
develop_password
`

6. Happy coding! 




### 🐬 MySQL

1. Go to the MySQL folder.

```bash
cd mysql
```

2. Check the provided `docker-compose.yaml` [for MySQL](./mysql/docker-compose.yaml) and change _db_, _username_ and _password_ if it is necessary.

3. Run the deployment. 

```bash
docker-compose up -d
```
`Note: There is a version that uses a seed, in case you want to test with a DB with data`
```
docker-compose -f docker-compose.seeded.yaml up -d
```

`Note: If you did not make any configuration changes, use the following values.`

4. Database name:
`
db
`

5. User:
`
db_user
`

6. Password:
`
db_password
`

7. Happy coding!




### 🐘 PostgreSQL 

1. Go to the Postgress folder.

```bash
cd postgress
```

2. Check the provider ` docker-compose.yml`[for PostgreSQL](./postgress/docker-compose.yaml) and change _password_ if it is necessary.

2. Run the deployment.

``` bash
docker-compose up -d
```
`Note: There is a version that uses a seed, in case you want to test with a DB with data`
```
docker-compose -f docker-compose.seeded.yaml up -d
```

`Note: If you did not make any configuration changes, use the following values.`

3. Database name:
`
postgres
`

4. User:
`
postgres
`

5. Password:
`
postgres
`

6. Happy coding!




###  🟥 Redis

1. Go to the Redis folder.

```bash
cd redis
```

2. Check the provider docker-compose.yml [for Redis](./redis/docker-compose.yaml). Because this project is for testing or development purposes, it is configured with _empty password_. 

3. Run the deployment.

```bash
docker-compose up -d
```

4. Happy coding!




###  🔰 ElasticSearch

1. Go to the ElasticSearch folder.

```bash
cd elasticsearch
```

2. Check the provider docker-compose.yml [for ElasticSearch](./elasticsearch/docker-compose.yaml) and make changes if it is necessary.

3. Run the deployment.

```bash
docker-compose up -d
```

` Note: This installation may take a long time. `

3. Make sure ElasticSearch is running correctly by typing following URL.

```bash
http://localhost:9200
```

You should see a JSON response with the information of the Elasticsearch instance.

4. Make sure Kibana is running correctly by typing the following URL.

```bash
http://localhost:9200
```

You should see the Kibana data visualization dashboard.

5. Happy coding!




### 📅 SqlServer

1. Go to the SQLServer folder.

```bash
cd sqlserver
```

2. Check the provider docker-compose.yml [for SqlServer](./sqlserver/docker-compose.yaml) and change _password_ if it is necessary.

3. Run the deployment.

```bash
docker-compose up -d 
```

`Note: There is a version that uses a seed, in case you want to test with a DB with data`

- Navigate to the path sqlserver/seeded

  ```bash
  cd sqlserver/seeded
  ```

- Run the command.

  ```
  docker-compose -f docker-compose.seeded.yaml up -d
  ```

`Note: If you did not make any configuration changes, use the following values.`

4. Default database name: `master`

5. Username: `sa`

6. Password: `password@123`

7. Happy coding!




### 📧 SMTP 

1. Go to the SMTP folder.

```bash
cd smtp
```

2. Check the provider [.env file](./smtp/.env) file and make changes if it is necessary.

3. Run the deployment.

```bash
docker-compose up -d
```

4.  Open a terminal and [create a reachable URL via Ngrok](Ngrok_example.md) with the following command.

```bash
 ngrok tcp 25 
```

`Note: If you did not make any configuration changes, use the following values.`

5. The username is `develop_user`

6. The password is `develop_password`

7. Happy coding!




### 🥑 ArangoDB

1. Go to the ArangoDB folder.

```bash
cd arangodb
```

2. Check the provider docker-compose.yml [for ArangoDB](./arangodb/docker-compose.yaml) and change _password_ if it is necessary.

3. Run the deployment.

```bash
docker-compose up -d
```

`Note: There is a version that uses a seed, in case you want to test with a DB with data`

```
docker-compose -f docker-compose.seeded.yaml up -d
```

4. Go to `http://localhost:8529` and Sign In with the credentials.

`Note: If you did not make any configuration changes, use the credentials below.`

5. Database name: `_system`

6. User: `root`

7. Password: `root_password`

8. Happy coding!


# Configuring other data sources 

### ➡️DynamoDB

1. Create an AWS [account](https://portal.aws.amazon.com/billing/signup#/start/email)
2. Enter the AWS shell, whether it is the cloud or the local
3. copy this command to create a table
```console
aws dynamodb create-table --table-name Music --attribute-definitions AttributeName=Artist,AttributeType=S AttributeName=SongTitle,AttributeType=S --key-schema AttributeName=Artist,KeyType=HASH AttributeName=SongTitle,KeyType=RANGE --provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5 --table-class STANDARD
```
4. We will verify that the table is active with the following command
```console 
aws dynamodb describe-table --table-name Music | grep TableStatus
```
5. Get your access credentials and your region




### 🪁 S3

1. Create an AWS [account](https://portal.aws.amazon.com/billing/signup#/start/email)
2. Enter the AWS shell, whether it is the cloud or the local
3. We create a s3 bucket: `aws s3 mb s3://bucket-appsmith `
4. We list our buckets: `aws s3 ls `





### 🔥 Firestore

1. We install [Gcloud](https://cloud.google.com/sdk/docs/install?hl=es-419)
2. We will follow the following commands.
3. We create a new project.
` gcloud projects create firestoreproject`
4. We list the project.
`gcloud project list `
5. We select the project
`gcloud config set project firestoreproject`
6. We create an application
`gcloud app create `
7. Create the database
`gcloud firestore databases create --region=us-east1 `
8. Database URL ` https://firestoreproject.firebaseio.com`