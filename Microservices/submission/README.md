# Microservices Containerization — Submission

## Architecture Overview

| Service          | Port | Description                                  |
|------------------|------|----------------------------------------------|
| User Service     | 3000 | Manages user data                            |
| Product Service  | 3001 | Handles product catalog                      |
| Order Service    | 3002 | Processes and tracks orders                  |
| Gateway Service  | 3003 | API gateway routing requests to all services |

---

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) (v20.10+)
- [Docker Compose](https://docs.docker.com/compose/install/) (v2.0+)
- Git

Verify installations:
```bash
docker --version
docker compose version
```

---

## Setup Instructions

### 1. Clone the Repository
```bash
git clone <your-forked-repo-url>
cd submission
```

### 2. Build and Start All Services
```bash
docker compose up --build
```

### 3. Verify All Containers Are Running
```bash
docker compose ps
```

All four services should show **Up** status.

---

## Testing Each Service

### User Service (Port 3000)
```bash
curl http://localhost:3000/users
```

### Product Service (Port 3001)
```bash
curl http://localhost:3001/products
```

### Order Service (Port 3002)
```bash
curl http://localhost:3002/orders
```

### Gateway Service (Port 3003)
```bash
curl http://localhost:3003/
```

> **Windows PowerShell users:** use `curl.exe` instead of `curl`

---

## Stopping the Services
```bash
docker compose down
```

---

## Troubleshooting

### Port Already in Use
**Error:** `Bind for 0.0.0.0:3000 failed: port is already allocated`

**Fix:** Find and stop the process using that port:
```bash
# Windows
netstat -ano | findstr :3000
taskkill /PID <PID> /F

# Mac/Linux
lsof -i :3000
kill -9 <PID>
```

---

### Container Exits Immediately
**Error:** A service shows `Exited` in `docker compose ps`

**Fix:** Check logs for that service:
```bash
docker compose logs user-service
docker compose logs product-service
docker compose logs order-service
docker compose logs gateway-service
```

---

### Services Can't Communicate
**Symptom:** Gateway returns connection refused when calling other services.

**Fix:** Ensure all services are on the same network in `docker-compose.yml` and use the service name as the hostname (e.g., `http://user-service:3000`).

---

## Screenshots

> *(Add your screenshots here showing services running)*

### docker compose ps — All services running
![docker compose ps](screenshots/docker-compose-ps.png)

### User Service Response
![User Service](screenshots/user-service.png)

### Product Service Response
![Product Service](screenshots/product-service.png)

### Order Service Response
![Order Service](screenshots/order-service.png)

### Gateway Service Response
![Gateway Service](screenshots/gateway-service.png)