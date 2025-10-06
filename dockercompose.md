# ساختار پیشنهادی ریپو
```
postgres-compose/
├─ docker-compose.yml
├─ .env.example
├─ Makefile
├─ .gitlab-ci.yml
└─ README.md
```
```bash
mkdir -p /root/apps/postgres
cd /root/apps/postgres
vim docker-compose.yml
```
```bash
docker compose up -d
docker compose logs -f postgres
```

create ```bash vim docker-compose.yml``` :
```bash
services:
  postgres:
    image: postgres:latest
    ports:
      - "5432:5432"
    environment:
      - POSTGRES_PASSWORD=psgresql_pass
      - POSTGRES_USER=psgresql_user
      - POSTGRES_DB=psgresql_db
      - PGDATA=/var/lib/postgresql/data
    volumes:
      - /root/apps/postgres:/var/lib/postgresql
    restart: always

```

for test : 
```bash
docker compose exec -it postgres psql -U <pg_user> -d <pg_db> -c "SELECT version();"
```

