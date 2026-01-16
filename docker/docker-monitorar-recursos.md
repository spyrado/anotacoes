# Monitoramento de Recursos

## Contexto

Eu posso ter mais de um docker rodando em uma máquina, com isso eu preciso administrar bem os recursos de cada maquina

  <img src="image.png" alt="alt text" width="600" />

## 🖥️ Configuração da máquina (host)

Imagine 1 máquina física ou VM com a seguinte capacidade total:

- CPU: 8 vCPUs
- Memória RAM: 16 GB
- Disco: 200 GB SSD

Essa é a capacidade máxima disponível para todos os containers juntos.

## 🐳 Containers rodando nessa máquina

Vamos rodar 3 containers Docker, cada um com uma responsabilidade diferente:

### 📦 Container 1 – API (backend)

Ex: API Node.js / NestJS

Limites definidos:

- CPU: 2 vCPUs
- Memória: 4 GB RAM
  ```
  --cpus="2" --memory="4g"
  ```

👉 Esse container nunca poderá usar mais que isso, mesmo que a máquina tenha recursos sobrando.

--- 

### 📦 Container 2 – Frontend

Ex: Angular / Nginx

Limites definidos:

- CPU: 1 vCPU
- Memória: 2 GB RAM

  ```
  --cpus="1" --memory="2g"
  ```

---

### 📦 Container 3 – Banco de dados

Ex: PostgreSQL

Limites definidos:

- CPU: 3 vCPUs
- Memória: 6 GB RAM

  ```
  --cpus="3" --memory="6g"
  ```

---

### 📊 Visão consolidada dos recursos

| Recurso | Máquina | Container 1 | Container 2 | Container 3 | Total usado |
| ------- | ------- | ----------- | ----------- | ----------- | ----------- |
| CPU     | 8 vCPU  | 2           | 1           | 3           | **6 vCPU**  |
| RAM     | 16 GB   | 4 GB        | 2 GB        | 6 GB        | **12 GB**   |

🔹 Sobra na máquina:

- CPU livre: 2 vCPUs
- Memória livre: 4 GB RAM
- Essa sobra é importante para:
  - Sistema operacional
  - Picos momentâneos
  - Evitar OOM (Out Of Memory)

---

### 🔧 Exemplo em docker-compose.yml

```yaml
version: "3.9"

services:
  api:
    image: minha-api
    deploy:
      resources:
        limits:
          cpus: "2.0"
          memory: 4g

  frontend:
    image: meu-frontend
    deploy:
      resources:
        limits:
          cpus: "1.0"
          memory: 2g

  database:
    image: postgres
    deploy:
      resources:
        limits:
          cpus: "3.0"
          memory: 6g

```