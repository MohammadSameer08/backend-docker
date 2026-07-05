# Docker Backend

A Node.js backend application containerized with Docker using a multi-stage build for optimized production images.

## Features

- **Multi-stage Docker build** — Separates build and production stages for smaller final image size
- **Node.js 22 Alpine** — Lightweight base image for reduced resource consumption
- **Port 3000** — Default application port (configurable)

## Prerequisites

- Docker installed on your system
- Node.js 22+ (for local development)
- npm or yarn

## Getting Started

### Build the Docker Image

```bash
docker build -t multi-stage-backend-docker .
```

### Run the Container

```bash
docker run -p 3000:3000 multi-stage-backend-docker
```

The application will start on `http://localhost:3000`

### Stop the Container

```bash
docker stop <container-id>
```

## Development

### Local Setup

```bash
npm install
npm start
```

### Install Dependencies

```bash
npm install nodemon --save-dev  # for auto-reload during development
```

## Docker Build Process

The Dockerfile uses a **two-stage build**:

1. **Builder Stage** — Installs all dependencies and copies source code
2. **Production Stage** — Copies only necessary files from builder, resulting in a smaller final image

This approach reduces image size and excludes development files from production.

## Environment Variables

Configure your application with environment variables. Create a `.env` file or pass them when running:

```bash
docker run -e NODE_ENV=production -p 3000:3000 multi-stage-backend-docker
```

## Troubleshooting

- **Port already in use:** Change the port mapping: `docker run -p 8000:3000 multi-stage-backend-docker`
- **Container exits immediately:** Check logs with `docker logs <container-id>`

## License

MIT