# NGINX Reverse Proxy with Golang and Python Services (Docker Compose)

## 📦 Structure

```
.
├── docker-compose.yml
├── nginx
│   ├── nginx.conf
│   └── Dockerfile
├── service_1
│   └── Dockerfile
├── service_2
│   └── Dockerfile
└── README.md
```

## 🚀 How to Run

1. Place your Golang service code in `service_1/`. It must listen on port **8081** and expose `/health` route.
2. Place your Python service (e.g., Flask) in `service_2/`. It must listen on port **8082** and expose `/health` route.

### ✅ Build and Run

```bash
docker-compose up --build
```

- Golang app: [http://localhost:8080/service1/](http://localhost:8080/service1/)
- Python app: [http://localhost:8080/service2/](http://localhost:8080/service2/)

## 🔍 Logs

To see NGINX logs with timestamps and paths:

```bash
docker logs <nginx-container-id>
```

## ❤️ Features

- Reverse proxy routing `/service1/` → Go backend
- `/service2/` → Python backend
- Healthchecks for both services
- Logging with timestamp and path in NGINX
- Everything runs on single port: `localhost:8080`
