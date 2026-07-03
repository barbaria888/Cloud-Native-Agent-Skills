# ☁️ Cloud Native Development with Google Cloud - AI Knowledge Skill

> *"An individual sitting in a coffee shop with merely a laptop and an internet connection has the power to design and deploy an application that can scale to millions of users."*
> — Martin Beeby, *Cloud Native Development with Google Cloud* (O'Reilly, 2024)

<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

## What Is This?

This repository is a **structured AI knowledge skill** synthesized from the O'Reilly book
[*Cloud Native Development with Google Cloud*](https://www.oreilly.com/library/view/cloud-native-development/9781098145088/)
by Martin Beeby.

It was built using the [**book-to-skill**](https://github.com/virgiliojr94/book-to-skill)
methodology — a philosophy for transforming technical books into **agent-ready,
token-efficient knowledge repositories** that AI coding assistants can load
on demand to give you expert-level guidance.

This is **not** a book summary. It is a living engineering reference:
- Mental models and decision frameworks
- Architecture patterns with GCP service mappings
- Production-grade gcloud / kubectl / Terraform command references
- Anti-patterns and when-to-use guidance
- Glossary of 60+ cloud native terms

<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

# How this helps you?
<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

###  Using This Skill with AI Coding Assistants

This repository follows the **book-to-skill** methodology and is designed to be consumed by AI coding assistants that support reusable Agent Skills or can use a local repository as context.

##  1. Clone the Repository

Clone this repository to your local machine:

```bash
git clone https://github.com/<your-username>/<your-repository>.git
cd <your-repository>
```

<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

## Claude Code

Install the repository as a local Agent Skill:

```bash
git clone https://github.com/<your-username>/<your-repository>.git \
~/.claude/skills/cloud-native-development-gcp
```

Start a new Claude Code session.

Example prompts:

```text
Explain Cloud Run using this skill.

Design a production-ready GKE deployment.

Show me the CI/CD pipeline described in the Factory chapter.

Compare Cloud SQL and Cloud Spanner using the guidance in this skill.
```

<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

## GitHub Copilot CLI

Install the repository into your skills directory:

```bash
git clone https://github.com/<your-username>/<your-repository>.git \
~/.copilot/skills/cloud-native-development-gcp
```

Reload your skills:

```text
/skills reload
```

The skill will now appear in your available skills.

<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

## Gemini CLI / Antigravity

Gemini CLI does **not** currently support the Agent Skills standard.

Instead, open this repository as your working directory or include it in your project context.

Recommended prompt:

```text
Use this repository as the authoritative reference.

Read SKILL.md first.

Use the chapter files, glossary, patterns, and cheatsheet before relying on general knowledge.
```

<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

## Other AI Coding Assistants

Any assistant capable of reading a local repository or Markdown documentation can use this project as a structured knowledge base.

Recommended workflow:

1. Read `SKILL.md`.
2. Navigate to the relevant chapter.
3. Use `patterns.md` for engineering patterns.
4. Use `glossary.md` for terminology.
5. Use `cheatsheet.md` for commands and quick reference.

<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

> **Note**
>
> This repository contains structured engineering knowledge—not executable code or plugins.
>
> Native Agent Skill support depends on your AI coding assistant.
> Other assistants can still use the repository effectively by loading it as project context.

<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

## Why This Exists

### For the Developer Community 🧑‍💻
<img width="1536" height="1024" alt="Image" src="https://github.com/user-attachments/assets/c28402b8-fecc-4122-ba00-48178dd603c9" />

Cloud native development on GCP has a steep learning curve. A developer new to
Google Cloud faces hundreds of services, dozens of CLI flags, and a whole new
set of architectural patterns to internalize.

This skill exists to **flatten that curve** — so that any developer (or their
AI assistant) can reason about GCP architecture, pick the right service, write
secure IAM policies, and ship production code faster.

The knowledge encoded here covers the full journey:
| Stage | What You Learn |
|---|---| 
| **Foundations** | Cloud native principles, GCP infrastructure, 12-factor app |
| **Build** | Microservices, containers, Cloud Run, Cloud Functions, GKE | 
| **Operate** | CI/CD with Cloud Build, IaC with Terraform |
| **Secure** | Zero-trust, IAM, Secret Manager, Cloud Armor, Workload Identity | 
| **Observe** | Logging, Monitoring, Tracing, OpenTelemetry, Alerting | 
| **Scale** | GKE Autopilot, Cloud Spanner, Memorystore |


### For the Cloud Native Ecosystem 🌐

The book introduces a beautiful mental model — **Laboratory, Factory, Citadel,
and Observatory** — four "facilities" every cloud native team needs.

By encoding this model into a skill that developers and AI agents can reference
daily, we help the cloud native community:

- Think in **platform terms**, not just individual services
- Build with **open standards** (OCI, Kubernetes, gRPC, OpenTelemetry) for
  portability without losing managed-service benefits
- Treat **observability and security as first-class design concerns**,
  not afterthoughts
- **Eliminate toil** with automation as a core cultural value

### For Google Cloud 💙

Google Cloud was built by cloud native engineers *for* cloud native engineers.
The abstractions in GCP — Borg, Colossus, Spanner, Andromeda — represent
decades of engineering investment to let developers focus on **code, not
infrastructure**.

This skill spreads that message to developers who may not yet know:
- Why GCP powers 70% of tech unicorns with only 10% market share
- How tools like Cloud Run, Cloud Build, and GKE Autopilot give individual
  developers superpower-level capabilities
- Why open-standards-first (not vendor-lock-in-first) is a viable and
  preferable architecture strategy on GCP

Every developer who learns to build cloud native on GCP — correctly — becomes
a force multiplier for the ecosystem.

<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

## How It Helps You

### If You're a Developer

Load the skill into your AI assistant and get instant, contextual help:

```
"Help me design a Cloud Run service with least-privilege IAM"
→ Agent loads ch06.md + ch04.md → gives you battle-tested patterns

"What's the difference between Cloud SQL and Cloud Spanner?"
→ Agent loads ch14.md → gives you a decision table, not a marketing page

"Show me a Cloud Build CI/CD pipeline"
→ Agent loads ch12.md → gives you working cloudbuild.yaml
```

### If You're Learning GCP

Use this as a structured study guide alongside the book:

1. Start with `SKILL.md` — get the big picture in 5 minutes
2. Read `chapters/ch01.md` through `ch03.md` — build the mental model
3. Follow the hands-on projects (`ch05` → `ch09`) with your own GCP account
4. Build your Laboratory (`ch10`), Factory (`ch12`), Citadel (`ch11`), and Observatory (`ch13`)

### If You're an Architect

Use `SKILL.md` as a decision-making reference:
- Runtime selection decision tree
- Lock-in mitigation strategies
- 12-factor compliance checklist
- Anti-pattern catalogue

<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

## Repository Structure

```
cloud-native-dev-gcp-skill/
├── SKILL.md              ← START HERE — master hub, mental models, index
├── README.md             ← This file
├── glossary.md           ← 60+ term definitions
├── cheatsheet.md         ← All CLI commands (gcloud / kubectl / terraform)
└── chapters/
    ├── ch01.md           ← What Is Cloud Native?
    ├── ch02.md           ← Why Google Cloud?
    ├── ch03.md           ← Cloud Native Applications (12-factor, microservices, DDD)
    ├── ch04.md           ← Preparing GCP (gcloud, IAM, service accounts)
    ├── ch05.md           ← Project 1: Tag Updater — Cloud Functions + BigQuery
    ├── ch06.md           ← Project 2: Skill Service — Cloud Run + buildpacks
    ├── ch07.md           ← Project 3: Fact Service — Cloud SQL + Identity Platform
    ├── ch08.md           ← Project 4: Profile Service — Firestore + Pub/Sub
    ├── ch09.md           ← Project 5: Frontend — Cloud Storage static hosting
    ├── ch10.md           ← Laboratory — Skaffold, Cloud Code, Minikube, inner loop
    ├── ch11.md           ← Citadel — Global LB, Cloud Armor, HTTPS, IAP
    ├── ch12.md           ← Factory — Cloud Build CI/CD, Terraform IaC
    ├── ch13.md           ← Observatory — Logging, Monitoring, Tracing, Alerts
    ├── ch14.md           ← Scaling — GKE Autopilot, Spanner, Workload Identity
    └── ch15.md           ← Going Further — certifications, community, next steps
```

<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

## The Four Facilities — At a Glance

```
┌─────────────────────────────────────────────────────────────┐
│                        GOOGLE CLOUD                         │
│                                                             │
│  🔬 LABORATORY          🏭 FACTORY                          │
│  Cloud Shell            Cloud Build                         │
│  Cloud Workstations     Artifact Registry                   │
│  Skaffold + Cloud Code  Cloud Deploy                        │
│  Minikube / GKE (dev)   Terraform                           │
│                                                             │
│  🏰 CITADEL             🔭 OBSERVATORY                      │
│  Cloud Run              Cloud Logging                       │
│  GKE Autopilot          Cloud Monitoring                    │
│  Cloud SQL / Spanner    Cloud Trace                         │
│  Secret Manager         OpenTelemetry                       │
│  Cloud Armor + IAP      Alerting Policies                   │
└─────────────────────────────────────────────────────────────┘
```

**The rule:** Immutable code artifacts flow Lab → Factory → Citadel.
The Observatory watches over everything.

<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

## Built With

| Tool / Resource | Purpose |
|---|---|
| [book-to-skill](https://github.com/virgiliojr94/book-to-skill) | Methodology for turning books into AI skills |
| [Cloud Native Development with Google Cloud](https://www.oreilly.com/library/view/cloud-native-development/9781098145088/) (O'Reilly) | Source book |
| [CNCF Landscape](https://landscape.cncf.io/) | Open standards reference |
| Google Cloud Documentation | Service-level accuracy |

<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

## Contributing

Found something wrong or out of date? Cloud evolves fast.

- Open a PR to update a chapter file with the latest API or service change
- Add new patterns as GCP releases new services
- Share how you've used this skill — community feedback makes it better

<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

## The Cloud Native Haiku

*(from Cloud Foundry, quoted in the book)*

```
Here is my source code
Run it on the cloud for me
I do not care how
```

That's the aspiration. This skill helps you get there — on Google Cloud,
the right way, with the right tools, and with enough understanding to own
every layer of the stack.

<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

## License

Knowledge synthesized from publicly available architectural patterns and
Google Cloud documentation. The book itself is © O'Reilly Media — please
support authors by purchasing the original.

This skill is shared freely for the developer community under the spirit of
open knowledge sharing. 🤝

<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

*Made with ❤️ for the cloud native community — because better-informed
developers build better products, and better products make everyone's
cloud infrastructure more reliable.*

<p align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=rect&color=0:4285F4,50:34A853,100:FBBC05&height=3&section=header"
    width="100%"
  />
</p>

