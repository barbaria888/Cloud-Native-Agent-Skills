---
name: cloud-native-dev-gcp
description: >
  Cloud-native development on Google Cloud Platform covering architecture
  principles, GKE, Cloud Run, Cloud Functions, CI/CD, observability, IaC
  (Terraform), and the Laboratory/Factory/Citadel/Observatory mental model.
triggers:
  - cloud native
  - google cloud
  - gcp architecture
  - gke
  - cloud run
  - cloud functions
  - terraform gcp
  - 12-factor
  - citadel factory laboratory observatory
  - microservices gcp
---

# Cloud Native Development with Google Cloud — Skill

## Core Mental Model: The Four Facilities

| Facility | Purpose | Key GCP Services |
|---|---|---|
| **Laboratory** | Developer productivity; rapid inner loop | Cloud Shell, Workstations, Skaffold, Cloud Code, Minikube |
| **Factory** | Automated build, test, delivery | Cloud Build, Artifact Registry, Cloud Deploy |
| **Citadel** | Secure, scalable production runtime | Cloud Run, GKE Autopilot, Cloud SQL, Spanner, Secret Manager, Cloud Armor |
| **Observatory** | Monitoring, logging, tracing | Cloud Logging, Cloud Monitoring, Cloud Trace, OpenTelemetry |

**Key rule:** Code flows Lab → Factory → Citadel as an **immutable artifact**.

## Cloud Native Architecture: 5 Pillars
1. Component independence (loosely coupled, independently deployable)
2. Built-in resilience (design for failure; multiple instances, auto-recovery)
3. Transparent observability (metrics/logs/traces as first-class citizens)
4. Declarative management (Kubernetes manifests, IaC — specify WHAT not HOW)
5. Zero-trust security (encrypt everywhere; verify every service interaction)

## Runtime Selection Decision Tree
```
Need a runtime?
  Occasional/event-driven glue code? → Cloud Functions (Gen 2)
  Long-running HTTP service?         → Cloud Run
  Need K8s control/portability?      → GKE Autopilot
  Full node control + networking?    → GKE Standard
```

## Lock-in Mitigation (Ranked by Portability)
1. Infrastructure-based (IaaS only) — most portable, fewest managed benefits
2. Kubernetes-based (managed K8s as common layer)
3. **Open-standards-based** ← *recommended* (OCI, Knative, PostgreSQL wire, gRPC)
4. Single-cloud (max managed services, max lock-in)

## 12-Factor + 3 Extensions Quick Reference
| # | Factor | GCP Implementation |
|---|---|---|
| I | Codebase | Git; 1 repo → many deploys |
| II | Dependencies | OCI Containers |
| III | Config | Env vars + Secret Manager |
| IV | Backing services | Attached via URI in config |
| V | Build/Release/Run | Cloud Build → Artifact Registry → Cloud Run/GKE |
| VI | Processes | Stateless containers |
| VII | Port binding | HTTP :8080 (Cloud Run default) |
| VIII | Concurrency | Horizontal scale (more instances) |
| IX | Disposability | Fast startup + graceful SIGTERM |
| X | Dev/Prod parity | Same containers + IaC |
| XI | Logs | stdout → Cloud Logging |
| XII | Admin processes | Cloud Scheduler + one-off Jobs |
| XIII | API First | gRPC / REST versioned contracts |
| XIV | Telemetry | OpenTelemetry → Cloud Monitoring |
| XV | Security | Least-privilege SAs + Secret Manager |

## Chapter Index (load chapters/chXX.md for detail)
| File | Topic |
|---|---|
| ch01 | Cloud native concepts, digital-native mindset |
| ch02 | GCP foundations: Borg, Colossus, Spanner, Andromeda |
| ch03 | Applications: 12-factor, microservices, DDD, containers |
| ch04 | Setup: gcloud, IAM, projects, service accounts |
| ch05 | Project 1 — Tag Updater: Cloud Functions + BigQuery + GCS + Scheduler |
| ch06 | Project 2 — Skill Service: Cloud Run, buildpacks, logging, perf |
| ch07 | Project 3 — Fact Service: Cloud SQL, Identity Platform, Spring Boot |
| ch08 | Project 4 — Profile Service: Firestore, Pub/Sub, event-driven |
| ch09 | Project 5 — Frontend: GCS static, API gateway, UI |
| ch10 | Laboratory: Skaffold, Cloud Code, Minikube, inner loop |
| ch11 | Citadel: Global LB, Cloud Armor, HTTPS, IAP, domain mapping |
| ch12 | Factory: Cloud Build CI/CD, Terraform IaC |
| ch13 | Observatory: Logging, Monitoring, Trace, OpenTelemetry, alerts |
| ch14 | Scaling: GKE Autopilot, Cloud Spanner, Workload Identity |
| ch15 | Going Further: certs, community, next steps |

## Top Anti-Patterns
- Lift-and-shift without redesigning for cloud failure modes
- DIY Kubernetes when managed services suffice
- Credentials in source code (secrets scanning is automated by attackers)
- Default service accounts (violates least-privilege)
- Not handling SIGTERM (violates disposability)
- State in container filesystem (breaks horizontal scaling)
- Premature microservice decomposition before hitting limitations
- Factory-only (no Laboratory) — kills developer innovation

## Key Command Snippets
```bash
# Auth & project
gcloud auth login
export PROJECT_ID=$(gcloud config get project)
gcloud config set project $PROJECT_ID

# Enable services
gcloud services enable run.googleapis.com cloudbuild.googleapis.com \
  artifactregistry.googleapis.com cloudfunctions.googleapis.com

# Least-privilege service account
gcloud iam service-accounts create $SA_NAME \
  --display-name "$SERVICE_NAME service account"
gcloud projects add-iam-policy-binding $PROJECT_ID \
  --member=serviceAccount:$SA_NAME@$PROJECT_ID.iam.gserviceaccount.com \
  --role=roles/run.invoker

# Cloud Run quick deploy
gcloud run deploy $SERVICE_NAME --source . --env-vars-file=.env.yaml \
  --no-allow-unauthenticated --service-account=$SA_NAME@$PROJECT_ID.iam.gserviceaccount.com
```
