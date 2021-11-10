# dynamodb-dockerfile
## What is this

A dockerfile which allows you to run DynamoDB locally.

## Docker run Examples

NB: the dynamo shell is at http://localhost:8000/shell

To run an ephemeral instance of DynamoDB:

```bash
docker run -p 8000:8000 krystan/dynamodb
```

If you want to data to live past the life of the container instance, mount a volume from your local host and set it as a the data directory:

```bash
docker run --rm -v ~/dynamodb_local_db/data:/dynamodb_local_db -p 8000:8000 krystan/dynamodb --dbPath /dynamodb_local_db
```

## Gotchas
The is really important if you are going to use a third party api (nodejs or something) you need to set the sharedDb flag for them all to use the same data and not
get seperate tables per client.

```bash
docker run -p 8000:8000 krystan/dynamodb -sharedDb
```

## Further reading
Amazons documentation for dynamodb local is [here](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/DynamoDBLocal.html)
## Motivation

I wanted a container that had dynamodb in it so i could develop if I didn't necessarily have access to aws.

## Installation

docker build -t yourtag .

## Comments

Have fun..
