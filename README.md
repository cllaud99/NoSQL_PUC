# Ambiente com MongoDB, Redis, PostgreSQL, Mongo-Express, Redis Commander e DBeaver (CloudBeaver)

Este `docker-compose` levanta um ambiente completo com bancos NoSQL e relacionais, além de interfaces administrativas web para facilitar o desenvolvimento local.

## Serviços incluídos

### 🟢 MongoDB (v6.0)
- Banco de dados NoSQL.
- Autenticação configurável via variáveis de ambiente.
- Porta: `27017`
- Volume persistente: `mongo_data`

### 🔴 Redis (v7.0)
- Banco de dados em memória, ideal para cache e filas.
- Porta: `6379`
- Volume persistente: `redis_data`

### 🌐 Mongo-Express (v1.0.0-alpha.4)
- Interface web para o MongoDB.
- Porta: `8081`
- Depende do MongoDB

### 🧰 Redis Commander
- Interface web para o Redis.
- Porta: `8082`
- Depende do Redis

### 🔵 PostgreSQL (v16)
- Banco de dados relacional SQL.
- Usuário, senha e nome do banco configuráveis.
- Porta: `5432`
- Volume persistente: `postgres_data`

### 🖥️ DBeaver (CloudBeaver)
- Interface web de administração para bancos relacionais (incluindo PostgreSQL).
- Porta: `8978`
- Já inicia com conexão automática ao PostgreSQL.

---

## Como usar

Para subir o ambiente em segundo plano:

¬¬¬bash
docker compose up -d
¬¬¬

Para parar o ambiente:

¬¬¬bash
docker compose down
¬¬¬

---

## Acesso aos serviços

| Serviço           | URL/Conexão                                       | Usuário / Senha         |
|------------------|---------------------------------------------------|--------------------------|
| MongoDB          | `mongodb://root:root123@localhost:27017`          | `root` / `root123`       |
| Redis            | `localhost:6379`                                  | (sem autenticação)       |
| Mongo-Express    | [http://localhost:8081](http://localhost:8081)    | `root` / `root123`       |
| Redis Commander  | [http://localhost:8082](http://localhost:8082)    | —                        |
| PostgreSQL       | `localhost:5432` (via cliente ou DBeaver)         | `admin` / `admin123`     |
| DBeaver Web      | [http://localhost:8978](http://localhost:8978)    | Conexão automática       |

---

## Variáveis de ambiente padrão

| Variável                   | Valor padrão  |
|----------------------------|---------------|
| MONGO_INITDB_ROOT_USERNAME| root          |
| MONGO_INITDB_ROOT_PASSWORD| root123       |
| MONGO_PORT                | 27017         |
| REDIS_PORT                | 6379          |
| POSTGRES_USER             | admin         |
| POSTGRES_PASSWORD         | admin123      |
| POSTGRES_DB               | mydatabase    |
| POSTGRES_PORT             | 5432          |

---

## Volumes

- `mongo_data`: persistência do MongoDB
- `redis_data`: persistência do Redis
- `postgres_data`: persistência do PostgreSQL
