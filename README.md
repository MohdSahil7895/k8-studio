# K8 Studio (Docker Distribution)

K8 Studio is a Kubernetes operations UI distributed as prebuilt Docker images.
This repository is intentionally **deployment-only** and contains only `docker-compose.yml` for running the product.

## What You Get

- Multi-context Kubernetes UI
- Pods, Deployments, StatefulSets, PVCs, Services
- Logs viewer and download
- Port forwarding from UI
- Environment variable view/edit workflows
- Resource monitoring (CPU/Memory)

## Screenshots

![K8 Studio settings view](./Screenshot%202026-02-24%20223809.png)
![K8 Studio logs view](./Screenshot%202026-02-24%20223830.png)
![K8 Studio pods terminal view](./Screenshot%202026-02-24%20223858.png)

## Supported Clusters

Any cluster reachable via your kubeconfig, including:

- Kubernetes (generic)
- GKE
- AKS
- EKS
- kind
- Docker Desktop Kubernetes

## Prerequisites

- Docker / Docker Desktop installed
- Access to your Kubernetes clusters (kubeconfig on host)
- If private images are used, Docker Hub login:

```bash
docker login
```

## Run K8 Studio

From this repository:

```bash
docker compose up -d
```

Open:

- `http://localhost:3453`

## Stop K8 Studio

```bash
docker compose down
```

## Pull Latest Images

```bash
docker compose pull
docker compose up -d
```

## Notes

- Backend runs internally on Docker network; only frontend UI is exposed.
- Kubernetes/cloud config directories are mounted from host as read-only.
- UI-managed port-forwarding uses the host port range configured in `docker-compose.yml`.

## Troubleshooting

- Contexts not visible:
  - verify kubeconfig: `kubectl config get-contexts`
- Port-forward URL not reachable:
  - ensure selected local port is within configured published range and not already in use
- Cluster auth issues:
  - refresh cloud auth session (`gcloud auth login`, `az login`, etc.)
