# Stack Docker Compose

Este proyecto contiene un **stack completo** utilizando Docker Compose, incluyendo:

- **Nginx** como reverse proxy.
- **Aplicación** (Node.js, Flask, etc.).
- **PostgreSQL** como base de datos.
- **Redis** para caching y colas.
- **Monitoring** con Prometheus y Grafana.

---

## Estructura del proyecto

```text
docker-compose/
├── docker-compose.yml
├── nginx/
├── app/
├── postgres/
├── redis/
├── monitoring/
└── README.md
