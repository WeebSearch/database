# Hasura Database

The weebsearch stack is split into isolated, modular containers where
most separate services rely on a common database.
This repo allows services to be built and developed separate from a
monolithic codebase by providing a reusable [Hasura](https://github.com/hasura/graphql-engine) container that has
an up-to-date schema and other useful tools.

### Usage

1. Spin up a `docker-compose.yaml` file

```yaml
services:
  postgres:
    container_name: postgres
    image: postgres
    environment:
      POSTGRES_DB: ws_username
      POSTGRES_USER: ws_password
      POSTGRES_PASSWORD: ws_database
  hasura:
    container_name: hasura
    image: weebsearch/hasura
    ports:
      - "8080:8080"
    environment:
      HASURA_GRAPHQL_DATABASE_URL: postgres://ws_username:ws_password@postgres/ws_database
      HASURA_GRAPHQL_ENABLE_CONSOLE: "true"
```

2. `docker-compose up`

### Todo

- [ ] Python database backup and restoration scripts for production

- [ ] Small amount of sample data

