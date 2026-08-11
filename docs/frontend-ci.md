# Frontend Repository – Developer Preview CI/CD

```mermaid
flowchart LR

subgraph CI["CI - Frontend Repo"]

A[Developer]
A --> B[Workflow Dispatch]
B --> C[Dependency Check]
C --> D[CodeQL]
D --> E[Secret Scan]
E --> F[KICS]
F --> G[Create Image Tag]
G --> H[Build Frontend Image]
H --> I[Verify Image<br/>in Harbor]
I --> J[Trivy Scan]

end

subgraph CD["CD - Helm Repo"]

K[Send Deployment<br/>Request]
K --> L[Repository Dispatch]
L --> M[Helm Chart Repo]
M --> N[Deploy Preview<br/>via Argo CD]
N --> O[Int-AP6 Cluster]
O --> P[Developer Preview]

end

J --> K
```
---

## Purpose

The Frontend repository is responsible for building and validating the frontend Docker image.

It **does not deploy directly to Kubernetes**.

Instead, after the Docker image has been successfully built and verified, it sends a **Repository Dispatch** event to the Helm Chart repository, which performs the deployment.

---

## Deployment Configuration

| Item        | Value                                                              |
| ----------- | ------------------------------------------------------------------ |
| Deployment  | Developer Preview                                                  |
| Trigger     | Manual (GitHub Actions)                                            |
| Branches    | `feature/*`, `bugfix/*`, `hotfix/*`, `chore/*`, `feat/*`, `docs/*` |
| Cluster     | Int-AP6 Cluster                                                    |
| Values File | `values-dev.yaml`                                                  |
| Purpose     | Individual developer preview                                       |

---

## GitHub Actions Workflow

The workflow performs the following steps.

1. Check Dependencies
2. CodeQL
3. Secret Scan
4. KICS
5. Create Frontend Docker Image Tag
6. Build Frontend Docker Image
7. Verify Frontend Image in Harbor Registry
8. Scan Frontend Image with Trivy
9. Send Deployment Request to Helm Repository

---

## Output

```
Frontend Source Code

↓

Docker Image

↓

Harbor Registry

↓

Repository Dispatch

↓

Helm Chart Repository
```

