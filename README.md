# EvoFit

Aplicación móvil para gimnasios: los socios con membresía vigente obtienen rutinas de entrenamiento (en el gimnasio o fuera de él) y planes alimenticios personalizados, y dan seguimiento diario a su cumplimiento. El gimnasio administra a sus socios y la vigencia de sus membresías.

Proyecto integrador de la asignatura **Gestión del Proceso de Desarrollo de Software** (Universidad Tecnológica de Aguascalientes, IDGS, grupo 10-B-11, septiembre–diciembre 2026).

## Integrantes

| Integrante | Rol |
|---|---|
| 230126 – Jolette Esmeralda Macías Valtierra | Scrum Master / DevOps |
| 230123 – Amanda Regina Lozano Cano | Desarrollo backend |
| 230135 – Ana Karen Ropón Campos | Desarrollo frontend |
| 230134 – Angela Guadalupe Ropón Campos | Base de datos y QA |

Docente: Jesús Bryan González Delgado

## Tecnologías

- **Frontend:** Ionic 8 + Angular + Capacitor
- **Backend:** Node.js 24 LTS + Express 5 (patrón MVC), JWT, bcrypt, Nodemailer
- **Base de datos:** MySQL 8
- **Servicios externos:** API Spoonacular
- **DevOps:** GitHub Actions, Docker, Docker Compose, Nginx, Prometheus, Grafana

## Estructura

```
evofit/
├── .github/workflows/   # CI (ci.yml) y CD (cd.yml)
├── frontend/            # App Ionic + Angular
├── backend/             # API REST Node.js + Express
│   ├── src/             # config, controllers, models, routes, middlewares, services
│   └── tests/           # unit, integration
├── database/            # schema.sql, seed.sql, procedures/
├── infra/               # docker-compose.yml, nginx/, monitoring/
├── docs/                # Documento integrador y diagramas
├── .env.example
└── README.md
```

## Requisitos

- Node.js 24 LTS y npm
- Ionic CLI (`npm i -g @ionic/cli`)
- Docker y Docker Compose v2
- Android Studio y JDK 17 (solo para compilar el APK)

## Instalación local

```bash
git clone https://github.com/[usuario-u-organizacion]/evofit.git
cd evofit
cp .env.example .env        # completar los valores
# Backend
cd backend && npm install && npm run dev
# Frontend (en otra terminal)
cd frontend && npm install && ionic serve
```

## Flujo de trabajo

- Ramas: `main` (producción), `develop` (integración), `feature/<issue>-<descripcion>`, `release/<version>`, `hotfix/<version>`.
- Todo cambio entra por pull request hacia `develop` con CI en verde y al menos una aprobación.
- Commits con [Conventional Commits](https://www.conventionalcommits.org/es/v1.0.0/): `tipo(ámbito): descripción`.
  - Tipos: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`, `build`, `ci`, `perf`.
  - Ámbitos: `frontend`, `backend`, `db`, `infra`, `docs`.
- Versionado semántico con etiquetas `vX.Y.Z` en `main`.

## Seguridad

Nunca subir archivos `.env`, contraseñas, tokens ni claves de API. Los secretos del pipeline se configuran en *Settings > Secrets and variables > Actions*.
