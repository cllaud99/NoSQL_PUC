# Ambiente com MongoDB, Redis, Mongo-Express e Redis Commander

Este docker-compose levanta quatro serviços importantes para desenvolvimento e administração de bancos NoSQL:

- **MongoDB** (versão 6.0): banco de dados NoSQL, com usuário e senha configuráveis via variáveis de ambiente.  
  Porta padrão exposta: 27017  
  Volume persistente para os dados.

- **Redis** (versão 7.0): banco de dados em memória, usado para cache e filas.  
  Porta padrão exposta: 6379  
  Volume persistente para os dados.

- **Mongo-Express** (versão 1.0.0-alpha.4): interface web para administração do MongoDB.  
  Porta padrão exposta: 8081  
  Depende do MongoDB para funcionar.

- **Redis Commander** (imagem oficial latest): interface web para administração do Redis.  
  Porta padrão exposta: 8082  
  Depende do Redis para funcionar.

## Como usar

Para subir o ambiente em background:

```bash
docker compose up -d
```

## Como acessar

- MongoDB:  
  URL para conexão: `mongodb://<usuário>:<senha>@localhost:27017`  
  Usuário e senha padrão: `root` / `root123`

- Redis:  
  Conectar em `localhost:6379` (sem senha configurada por padrão)

- Mongo-Express (interface web MongoDB):  
  Abra no navegador: [http://localhost:8081](http://localhost:8081)  
  Use o mesmo usuário e senha do MongoDB.

- Redis Commander (interface web Redis):  
  Abra no navegador: [http://localhost:8082](http://localhost:8082)

## Parar o ambiente

```bash
docker compose down
```

---

## Variáveis de ambiente padrão

| Variável                  | Valor padrão |
|---------------------------|--------------|
| MONGO_INITDB_ROOT_USERNAME | root         |
| MONGO_INITDB_ROOT_PASSWORD | root123      |
| MONGO_PORT                 | 27017        |
| REDIS_PORT                 | 6379         |

---

## Volumes

- `mongo_data`: para persistir dados do MongoDB  
- `redis_data`: para persistir dados do Redis
