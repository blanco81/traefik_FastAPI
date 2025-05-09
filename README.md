# traefik_FastAPI

Traefik Reverse Proxy para Microservicios FastAPI

Este proyecto demuestra cómo configurar un entorno de microservicios basado en **FastAPI** gestionado por el **proxy inverso Traefik**. Está diseñado para enrutar múltiples servicios web utilizando un único punto de entrada (puerto 80), facilitando el desarrollo modular y escalable de aplicaciones web modernas.

---

## Estructura del Proyecto

```
traefik_FastAPI/
├── docker-compose.yml
├── traefik/
│   ├── traefik.yml          # Configuración estática de Traefik
│   └── config.yml           # (opcional) Configuración dinámica (middlewares, etc.)
├── service1/
│   ├── Dockerfile
│   └── main.py              # Aplicación FastAPI para /service1
├── service2/
│   ├── Dockerfile
│   └── main.py              # Aplicación FastAPI para /service2
```

---

## ¿Qué incluye?

- **Docker Compose**: para levantar los servicios y Traefik fácilmente.
- **FastAPI**: dos microservicios independientes escuchando en el puerto `8000`.
- **Traefik**:
  - Descubrimiento automático de contenedores.
  - Ruteo por prefijo de URL (`/service1`, `/service2`).
  - Eliminación del prefijo (middleware `stripPrefix`).
  - Reintentos automáticos (middleware `retry`).
  - Panel de administración (`http://localhost:8080/dashboard`).

---

## Requisitos

- Docker
- Docker Compose

---

## Cómo usar

1. Clona este repositorio:
   ```bash
   git clone https://github.com/tuusuario/traefik_FastAPI.git
   cd traefik_FastAPI
   ```

2. Levanta los contenedores:
   ```bash
   docker-compose up --build
   ```

3. Accede a los servicios:

   - FastAPI Service 1:
     ```bash
     curl http://localhost/service1/
     curl http://localhost/service1/health
     ```

   - FastAPI Service 2:
     ```bash
     curl http://localhost/service2/
     curl http://localhost/service2/health
     ```

   - Dashboard de Traefik:
     ```
     http://localhost:8080/dashboard/
     ```

---

## Extensiones posibles

- Autenticación para el dashboard de Traefik.
- HTTPS con Let's Encrypt.
- Escalado horizontal de servicios.
- Integración con base de datos o servicios externos.

---

## Licencia

Este proyecto es de uso libre para fines educativos y de desarrollo.
