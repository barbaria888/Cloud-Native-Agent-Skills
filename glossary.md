# Glossary — Cloud Native Development with Google Cloud

| Term | Definition |
|---|---|
| **Andromeda** | Google's software-defined networking layer managing bandwidth across GCP |
| **Artifact Registry** | GCP managed container/artifact registry (replaces Container Registry) |
| **Autopilot (GKE)** | Fully managed GKE mode; pay per pod, not per node |
| **BigQuery** | GCP serverless data warehouse; SQL analytics at petabyte scale |
| **Borg** | Google's internal cluster management system; Kubernetes was inspired by it |
| **Bounded Context** | DDD concept: explicit boundary within which a model applies |
| **Buildpack** | OCI-standard tool that auto-detects language and builds container images |
| **CNCF** | Cloud Native Computing Foundation; governs Kubernetes, OpenTelemetry, etc. |
| **Citadel** | Book's metaphor for the secure production runtime environment |
| **Cloud Armor** | GCP Web Application Firewall (WAF) and DDoS protection |
| **Cloud Build** | GCP managed CI/CD build service |
| **Cloud Code** | IDE plugin (VS Code / JetBrains) with K8s/Cloud Run dev tools |
| **Cloud Deploy** | GCP managed continuous delivery service for K8s |
| **Cloud Firestore** | GCP serverless NoSQL document database |
| **Cloud Functions** | GCP serverless function runtime (event-driven, Gen 2 = Cloud Run-based) |
| **Cloud Logging** | GCP centralized log aggregation and querying service |
| **Cloud Monitoring** | GCP metrics collection, dashboards, and alerting service |
| **Cloud Pub/Sub** | GCP global message broker (at-least-once delivery) |
| **Cloud Run** | GCP serverless container runtime (HTTP/gRPC, scales to zero) |
| **Cloud Scheduler** | GCP managed cron-like job scheduler |
| **Cloud SQL** | GCP managed relational database (PostgreSQL, MySQL, SQL Server) |
| **Cloud Spanner** | GCP globally-distributed, strongly-consistent relational database |
| **Cloud Storage** | GCP object storage (equivalent to S3) |
| **Cloud Trace** | GCP distributed tracing service |
| **Cloud Workstations** | GCP managed developer virtual workstations |
| **Colossus** | Google's distributed storage system underpinning GCS, BigQuery etc. |
| **ConfigMap** | Kubernetes object for non-secret configuration key-value pairs |
| **Contract Testing** | Verifying the agreed API contract between two microservices |
| **DDD** | Domain-Driven Design; technique to define microservice boundaries |
| **DevOps** | Practices combining Dev + Ops; "you build it, you run it" |
| **Digital Native** | Organisation/developer designed for cloud from inception |
| **Disposability** | 12-factor IX: containers are ephemeral; fast startup, graceful shutdown |
| **Event Storming** | Collaborative workshop to map event flow in a domain |
| **Factory** | Book's metaphor for the automated CI/CD build and test pipeline |
| **GKE** | Google Kubernetes Engine — managed Kubernetes service |
| **gcloud CLI** | Google Cloud command-line tool for all GCP API interactions |
| **Golden Signals** | SRE's four key metrics: Latency, Traffic, Errors, Saturation |
| **gRPC** | High-performance RPC framework using Protocol Buffers; binary protocol |
| **gsutil** | CLI tool for Cloud Storage operations |
| **IAM** | Identity and Access Management — GCP's auth/authz system |
| **IAP** | Identity-Aware Proxy — protects GCP services with identity-based access |
| **IaC** | Infrastructure as Code (Terraform, Pulumi, Deployment Manager) |
| **Jib** | Google's container-build tool for JVM apps (no Dockerfile needed) |
| **Jupiter** | Google's high-speed intra-datacenter network fabric |
| **k9s** | Terminal-based Kubernetes cluster management UI |
| **Knative** | Kubernetes-based platform for serverless/event-driven workloads |
| **Ko** | Tool to build Go container images without Docker |
| **Laboratory** | Book's metaphor for the developer productivity environment |
| **Least Privilege** | Security principle: grant minimum permissions needed |
| **LQL** | Logging Query Language used in Google Cloud Logging |
| **Memorystore** | GCP managed Redis/Memcached in-memory cache service |
| **Microservice** | Small, independently deployable service with single responsibility |
| **Minikube** | Local Kubernetes cluster for development |
| **Monolith** | Single deployable unit containing all functionality |
| **OCI** | Open Container Initiative; standard for container images and runtimes |
| **OpenTelemetry** | CNCF standard for traces, metrics, logs; multi-cloud portable |
| **Observatory** | Book's metaphor for monitoring, logging, alerting, and tracing |
| **Pod** | Smallest deployable Kubernetes unit; holds one or more containers |
| **Project (GCP)** | GCP resource container for billing, IAM, and service grouping |
| **Pub/Sub** | See Cloud Pub/Sub |
| **Region** | Geographic area with 3-4 availability zones in GCP |
| **Secret Manager** | GCP managed secret storage with versioning, audit, and rotation |
| **Service Account** | Non-human identity used by GCP services and applications |
| **Service Mesh** | Infrastructure layer for service-to-service communication (Istio) |
| **Skaffold** | CLI tool for K8s inner-loop dev: build, push, deploy on save |
| **Span** | A single timed operation within a distributed trace |
| **Spanner** | See Cloud Spanner |
| **SRE** | Site Reliability Engineering — Google's operations methodology |
| **Stateless** | 12-factor VI: no in-memory or local disk state; store state externally |
| **TFLint** | Linter for Terraform configurations |
| **TFSec** | Security scanner for Terraform configurations |
| **Terraform** | HashiCorp IaC tool; declarative infrastructure provisioning |
| **Testcontainers** | Library for Docker-based integration testing |
| **Trie** | Tree data structure optimised for prefix-based string lookup |
| **TrueTime** | Google's globally synchronised atomic clock API used by Spanner |
| **VPC** | Virtual Private Cloud — GCP's software-defined network |
| **Workload Identity** | GCP mechanism to bind K8s service accounts to GCP service accounts |
| **XP** | Extreme Programming; agile methodology emphasising TDD, small releases |
| **Zone** | Single datacenter-like location within a GCP region |
