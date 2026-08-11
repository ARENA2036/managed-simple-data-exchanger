# Backend Repository – Developer Preview CI/CD

```mermaid
flowchart LR

subgraph CI["CI - Backend Repo"]

A[Developer]
A --> B[Workflow Dispatch]
B --> C[Dependency Check]
C --> D[CodeQL]
D --> E[Secret Scan]
E --> F[KICS]
F --> G[Create Backend Docker Image Tag]
G --> H[Build Backend Docker Image]
H --> I[Verify Backend Image<br/>in Harbor Registry]
I --> J[Scan Backend Image<br/>with Trivy]

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

The Backend repository builds and validates the backend Docker image.

It **does not deploy directly**.

After the image passes all quality and security checks, it sends a deployment request to the Helm Chart repository.

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

1. Check Dependencies
2. CodeQL
3. Secret Scan
4. KICS
5. Create Backend Docker Image Tag
6. Build Backend Docker Image
7. Verify Backend Image in Harbor Registry
8. Scan Backend Image with Trivy
9. Send Deployment Request to Helm Repository

---

## Output

```
Backend Source Code

↓

Docker Image

↓

Harbor Registry

↓

Repository Dispatch

↓

Helm Chart Repository
```
