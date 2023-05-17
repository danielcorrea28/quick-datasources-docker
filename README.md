# Docker Datasources

This project aims to provide quick and easy steps for configuring database services so that you can start programming and testing as soon as possible.

## Notes

- The deployment instructions provided here are not suited for production use, please use them for testing and POCs only.
- On Linux, docker commands must be run as administrator.
- If you are deploying this on a hosting provider, you will need to use `Ngrok` to get a usable URL to connect to. If you use this locally, just remember to use `localhost`.

- Example how to get Ngrok host and port to make connections.
```console
appsmith@ngrok:~$ ngrok tcp 3306
Session Status   
online                                                                                   
Account                       Appsmith-svg (Plan: Free)                                                                  
Version                       3.1.0                                                                                     
Region                        Europe (eu)                                                                               
Latency                       164ms                                                                                    
Web Interface                 http://127.0.0.1:4040                                                                     
Forwarding                    tcp://0.tcp.eu.ngrok.io:16696 -> localhost:3306 
Connections                  
ttl     opn     rt1     rt5     p50     p90                                                                            
0       0       0.00    0.00    0.00    0.00                                                                                 
```

- For example, the host and the port to make that connection would be.

`host: 0.tcp.eu.ngrok.io`
`port: 16696`

## General Requirements

- [Docker](https://docs.docker.com/engine/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)
- [Ngrok](https://ngrok.com/) (Optional)


## Service Setup

### 🌿 MongoDB

1. Copy the provided `docker-compose.yaml` [for MongoDB](MongoDB/docker-compose.yaml).

2. Run the deployment. 

```bash
docker-compose up -d
```
`Note: There is a version that uses a seed, in case you want to test with a DB with data`

```
docker-compose -f docker-compose.seeded.yaml up -d
```

3. User
`
develop_user
`

4. Password
`
develop_password
`

5. Happy coding! 




### 🐬 MySQL

1. Copy the provided `docker-compose.yaml` [for MySQL](Mysql/docker-compose.yaml).

2. Run the deployment. 

```bash
docker-compose up -d
```
`Note: There is a version that uses a seed, in case you want to test with a DB with data`
```
docker-compose -f docker-compose.seeded.yaml up -d
```

3. Database name
`
db
`

4. User
`
db_user
`

5. Password
`
db_password
`

6. Happy coding!




### 🐘 PostgreSQL 

1. Copy the provider ` docker-compose.yml`[for PostgreSQL](/Postgress/docker-compose.yaml)

2. Run the deployment.

``` bash
docker-compose up -d
```
`Note: There is a version that uses a seed, in case you want to test with a DB with data`
```
docker-compose -f docker-compose.seeded.yaml up -d
```

3. Database name
`
postgres
`

4. User
`
postgres
`

5. Password
`
postgres
`

6. Happy coding!




###  🟥 Redis

1. Copy the provider docker-compose.yml [for Redis](/Redis/docker-compose.yaml).

2. Run the deployment.

```bash
docker-compose up -d
```

3. Happy coding!




###  🔰 ElasticSearch

1. Copy the provider docker-compose.yml [for ElasticSearch](/ElasticSearch/docker-compose.yaml).

` Note: This installation may take a long time. `

2. Run the deployment.

```bash
docker-compose up -d
```

3. Make sure Elasticsearch is running correctly by typing following URL.

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




### SqlServer

1. Copy the provider docker-compose.yml [for SqlServer](/SqlServer/docker-compose.yaml).

2. Run the deployment.

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

5. Default database name: `master`

6. Username: `sa`

7. Password: `password@123`

8. Happy coding!




### 📧 SMTP 

1. Copy the provider docker-compose.yml [for SMTP](/SMTP/docker-compose.yaml)

2. Run the deployment.

```bash
docker-compose up -d
```

3.  Open a terminal and create a reachable URL via Ngrok with the following command.

```bash
 ngrok tcp 25 
```

4. The username is `develop_user`

5. The password is `develop_password`

6. Happy coding!




### 🥑 ArangoDB
1. Copy the provider docker-compose.yml [for ArangoDB](/ArangoDB/docker-compose.yaml)
```yaml
version: '3.7'
services:
  arangodb_db_container:
    image: arangodb:3.2.2
    environment:
      ARANGO_ROOT_PASSWORD: appsmith
    ports:
      - 8529:8529
```
2. Run the deployment.
```bash
docker-compose up -d docker-compose.yaml 
```
`Note: There is a version that uses a seed, in case you want to test with a DB with data`
```
docker-compose -f docker-compose.seeded.yaml up -d
```
3. Open a terminal and create a reachable URL via Ngrok with the following command.
 ```bash
ngrok tcp 8529
```
4. Follow our guide to create an [ArangoDB](https://docs.appsmith.com/reference/datasources/querying-arango-db)
   - Use the URL provided by the Ngrok command as the *host* in your connection settings.
5. Database name:` _system`
6. User: `appsmith`
7. Password: `appsmith `
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
6. Follow our guide to create a [DynamoDB](https://docs.appsmith.com/reference/datasources/querying-dynamodb)
### 🪁 S3
1. Create an AWS [account](https://portal.aws.amazon.com/billing/signup#/start/email)
2. Enter the AWS shell, whether it is the cloud or the local
3. We create a s3 bucket: `aws s3 mb s3://bucket-appsmith `
4. We list our buckets: `aws s3 ls `
5. Follow our guide to create a [S3](https://docs.appsmith.com/reference/datasources/querying-amazon-s3)

### 🔥 Firestore

1. We install [Gcloud](https://cloud.google.com/sdk/docs/install?hl=es-419)
2. We will follow the following commands.
3. We create a new project.
` gcloud projects create appsmithfirestore`
4. We list the project.
`gcloud project list `
5. We select the project
`gcloud config set project appsmithfirestore `
6. We create an application
`gcloud app create `
7. Create the database
`gcloud firestore databases create --region=us-east1 `
8. Database URL ` https://appsmithfirestore.firebaseio.com`
9. Follow our guide to creating a [Firestore](https://docs.appsmith.com/v/v1.2/datasource-reference/querying-firestore)


