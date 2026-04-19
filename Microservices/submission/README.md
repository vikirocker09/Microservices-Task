# Microservices Containerization — Submission

## Architecture Overview

 Service          |  Port | Description                                  |

| User Service     |  3000 | Manages user data                            |
| Product Service  | 3001 | Handles product catalog                      |
| Order Service    |  3002 | Processes and tracks orders                  |
| Gateway Service  | 3003 | API gateway routing requests to all services |

---

## Prerequisites

- [Docker]
- [Docker Compose]
- Git

Verify installations:

docker --version
docker compose version




## Setup Instructions

### 1. Clone the Repository

git clone https://github.com/vikirocker09/Microservices-Task.git

### 2. Build and Start All Services

docker compose up --build


### 3. Verify All Containers Are Running

docker compose ps


All four services should show **Up** status.

---

## Testing Each Service

### User Service (Port 3000)

 http://localhost:3000/users


### Product Service (Port 3001)

 http://localhost:3001/products


### Order Service (Port 3002)

curl http://localhost:3002/orders


### Gateway Service (Port 3003)

curl http://localhost:3003/

## Troubleshooting


---

### Container Exits Immediately
**Error:** A service shows `Exited` in `docker compose ps`

**Fix:** Check logs for that service:

docker compose logs user-service
docker compose logs product-service
docker compose logs order-service
docker compose logs gateway-service


---



## Screenshots
<img width="1658" height="641" alt="image" src="https://github.com/user-attachments/assets/d822f192-f515-432a-b97a-11d343ffdae9" />
<img width="1905" height="942" alt="image" src="https://github.com/user-attachments/assets/1063701b-d312-41c4-a74a-8ea613c2ac5c" />
<img width="1491" height="289" alt="image" src="https://github.com/user-attachments/assets/7c131a60-8351-42d6-aaed-a20b8f97616e" />
<img width="1833" height="364" alt="image" src="https://github.com/user-attachments/assets/6a03283d-510b-469a-aec8-4c3e5828b6b1" />
<img width="1807" height="337" alt="image" src="https://github.com/user-attachments/assets/50d22869-147f-4329-807c-5c01acf2b208" />
<img width="1910" height="513" alt="image" src="https://github.com/user-attachments/assets/065c9679-9332-42ca-8abf-ff5099011e9c" />


### Order Service Response
![Order Service](screenshots/order-service.png)

### Gateway Service Response
![Gateway Service](screenshots/gateway-service.png)
