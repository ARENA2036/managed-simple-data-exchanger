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
F --> G[Build Backend Image]
G --> H[Verify Image<br/>in Harbor]
H --> I[Trivy Scan]

end

subgraph CD["CD - Helm Repo"]
I[Send Deployment<br/>Request]
I --> K[Repository Dispatch]
K --> L[Helm Chart Repo]
L --> M[Deploy Preview<br/>via Argo CD]
M --> N[Int-AP6 Cluster]
N --> O[Developer Preview]

end

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
5. Build Backend Docker Image
6. Verify Backend Image in Harbor Registry
7. Scan Backend Image with Trivy
8. Send Deployment Request to Helm Repository

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
