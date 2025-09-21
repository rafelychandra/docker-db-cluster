# Sample PostgreSQL with Docker

This project provides a simple PostgreSQL setup using **Docker** and **Docker Compose**.  
It runs a Postgres 16 container with a persistent volume so your data is not lost when the container stops.

---

## 📦 Requirements
- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/)

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone <your-repo-url>
```

### 2. Start PostgreSQL
```bash
docker-compose up -d
```

### 3. Connecting to the Database
Using psql
```bash
psql -h localhost -p 5431 -U sample-user -d sample-db
```
You can set your db config
```bash
Using GUI Tools
pgAdmin, TablePlus, or DBeaver
Host: localhost
Port: 5431
Database: sample-db
User: sample-user
Password: sample-password
```
### 4. Test the Database
```sql
-- Create a table
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL
);

-- Insert some data
INSERT INTO users (name, email) VALUES
('Alice', 'alice@example.com'),
('Bob', 'bob@example.com');

-- Query data
SELECT * FROM users;
```
### 5. Container Management
- View running containers
```bash
docker ps
```
- Stop the containers
```bash
docker-compose down
```
- Stop and remove containers with volumes (⚠️ deletes all data)
```bash
docker-compose down -v
```
- Remove the database volume only
```bash
docker volume rm <project-folder>_postgres_data
```