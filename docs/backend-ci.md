# Backend Repository – Developer Preview CI/CD

```mermaid
flowchart LR

subgraph CI["CI - Backend Repo"]
direction TB

A[Developer]
B[Workflow Dispatch]
C[Check Dependencies]
D[CodeQL]
E[Secret Scan]
F[KICS]
H[Build Backend<br/>Docker Image]
I[Push Backend Image<br/>to Harbor]
J[Verify Backend Image<br/>in Harbor]
K[Trivy Image Scan]

A --> B

B --> C
B --> D
B --> E
B --> F

C --> H
D --> H
E --> H
F --> H

H --> I
I --> J
J --> K

end

subgraph CD["CD - Helm Chart Repo"]
direction TB

L[Send Deployment<br/>Request]
M[Repository Dispatch]
N[Helm Chart Repo]
O[Deploy Preview<br/>via Argo CD]
P[Int-AP6 Cluster]
Q[Developer Preview<br/>Unique Argo CD App<br/>Unique Namespace]

L --> M
M --> N
N --> O
O --> P
P --> Q

end

K --> L
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