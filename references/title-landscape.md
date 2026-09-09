# AI Engineering Title Landscape

**Last researched: 2026-09-09.** Verified against real 2025–2026 job postings
(LinkedIn, Greenhouse, Lever, Ashby, company career pages) and credible
industry articles — not assumed from title names.

**Staleness rule:** AI job titles move fast (see AI-Forward Engineer below —
a real question people ask, answered by checking real postings rather than
guessing from the name). Before reusing this file: if the "Last researched"
date above is more than **~90 days** old, or the person's report needs a
title that isn't covered here, redo Step 1's web research and overwrite this
whole file with a fresh dated snapshot — don't patch individual lines,
regenerate it, since the point is one coherent snapshot per research pass.
Because this repo is git-tracked, `git log -- references/title-landscape.md`
is the history of how the landscape has changed over time; a diff between two
snapshots is often interesting on its own — this is also where a title that
used to be real and has since faded (the way Prompt Engineer did) would show
up as a removal, not just silently vanish.

## Table of contents

- [Overview](#overview)
- [Skills × titles matrix](#skills--titles-matrix)
- [Field guide entries](#field-guide-entries)
  - [Family: Foundation-model application engineering](#family-foundation-model-application-engineering)
  - [Family: Model & infrastructure engineering](#family-model--infrastructure-engineering)
  - [Family: Customer-facing delivery](#family-customer-facing-delivery)
- [Cross-cutting skillset](#cross-cutting-skillset)
- [What actually differentiates titles](#what-actually-differentiates-titles)

## Overview

| Title | Status | In one line | Closest adjacent titles |
|---|---|---|---|
| AI Engineer | Established | Builds products on top of foundation models via API: RAG, prompting, evals, agent glue. | Applied AI Engineer, Agentic Engineer |
| Applied AI Engineer | Established | A customer- or deployment-facing AI Engineer: helps outside teams put a company's models into production. | AI Engineer, Forward Deployed Engineer |
| Agentic Engineer | Emerging | Specializes in multi-step, tool-using agents: orchestration, memory, guardrails, agent evals. | AI Engineer, Applied AI Engineer |
| Machine Learning Engineer | Established | Builds and trains models from data: features, training loops, tuning, deployment of the artifact. | MLOps Engineer, AI Engineer |
| MLOps Engineer | Established | Owns the operational lifecycle of models already built: CI/CD, monitoring, drift, scaling, cost. | Machine Learning Engineer, DevOps Engineer |
| AI Solutions Architect | Established | Pre-sales and design-led: scopes and architects enterprise AI systems, hands off most of the build. | Forward Deployed Engineer |
| Forward Deployed Engineer | Established, expanding fast | Embeds on-site with a customer to build and ship production AI on their own data and infrastructure. | Applied AI Engineer, AI Solutions Architect |
| AI Product / Founding AI Engineer | Established at startups | A full-stack generalist who owns a product area end to end; AI is one skill among several, not the whole job. | AI Engineer |
| AI-Forward Engineer | **Not a title** | Not a standalone role. Either a shorthand inside "Forward Deployed Engineer," or a culture label for a team. | Forward Deployed Engineer |

> **Dropped from tracking: Prompt Engineer.** It was a real standalone title
> through ~2024 but had "all but disappeared" as one by mid-2025 (Fast
> Company), folded into AI Engineer / Applied AI Engineer / Agentic Engineer
> postings and reframed as "context engineering." Since it no longer names an
> independent role to score fit against, it's excluded from this landscape
> rather than kept as a permanently-declining placeholder. If postings
> re-emerge under this title, re-add it on the next research pass.

**"AI-Forward Engineer" in detail.** No company was found posting a standalone
role literally titled this, distinct from the others above. It surfaces two
other ways:

- **Inside a Forward Deployed Engineer name.** Databricks runs a team called
  "AI Forward Deployed Engineering (AI FDE)," posting roles like "AI Engineer
  – FDE (Forward Deployed Engineer)." Here "AI-forward" is shorthand inside
  the FDE name, not a separate role.
- **As a culture descriptor.** Writing on "AI-pilled" / "AI-native"
  engineering teams uses "AI-forward" to describe a team that has
  restructured its workflow around AI tools and coding agents — a description
  of how a team works, not a job function anyone is hired into.

If a posting or a person uses this phrase, read it as a synonym for Forward
Deployed Engineer or Applied AI Engineer, or as a culture description, not as
a distinct species. Sources: [Databricks, AI Forward Deployed
Engineering](https://www.databricks.com/company/careers/professional-services/sr-manager-ai-forward-deployed-engineering-fde-8414367002) ·
[Bessemer, Inside AI-pilled engineering
teams](https://www.bvp.com/atlas/inside-ai-pilled-engineering-teams-five-lessons-for-scaling-without-losing-the-plot)

## Skills × titles matrix

Nineteen skills against the eight real titles ("AI-Forward Engineer" excluded,
since it isn't an independent role to score). **●** = core to the role, named
as a real requirement. **◐** = common, but a supporting skill rather than the
center of the job. Blank = rarely part of this title's scope.

| Skill | AI Eng | Applied AI | Agentic | ML Eng | Sol. Arch | FDE | MLOps | Founding |
|---|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| **Building & integration** | | | | | | | | |
| Python | ● | ● | ● | ● | ◐ | ● | ● | ● |
| Shipping to production, not just prototypes | ● | ● | ● | ◐ | ◐ | ● | ◐ | ● |
| LLM / foundation-model API integration | ● | ● | ● | ◐ | ◐ | ● | | ● |
| RAG pipelines (embeddings, vector DBs, retrieval) | ● | ◐ | ◐ | ◐ | ◐ | ◐ | | ◐ |
| Prompt / context engineering | ● | ● | ● | | ◐ | ● | | ◐ |
| Agent orchestration (LangGraph, CrewAI, MCP) | ◐ | ◐ | ● | | ◐ | ◐ | | ◐ |
| Evaluation design (LLM-as-judge, eval harnesses) | ● | ● | ● | ◐ | | ● | | ◐ |
| **Model & data** | | | | | | | | |
| Model training / fine-tuning from scratch | | ◐ | | ● | | | ◐ | |
| Feature engineering & classic ML pipelines | | | | ● | | | ◐ | |
| **Infrastructure & operations** | | | | | | | | |
| Cloud infra (AWS / GCP / Azure) | ◐ | ◐ | ◐ | ◐ | ● | ◐ | ● | ◐ |
| CI/CD & infrastructure-as-code | | | ◐ | ◐ | ◐ | | ● | ◐ |
| Containerization / orchestration (Docker, K8s) | | | | ◐ | ◐ | | ● | |
| Production monitoring & drift observability | ◐ | ◐ | ● | ◐ | | ◐ | ● | |
| **People & business** | | | | | | | | |
| Client-facing / customer embedding | | ● | | | ● | ● | | ◐ |
| Pre-sales feasibility & architecture scoping | | ◐ | | | ● | ◐ | | |
| Product sense, pricing, roadmap ownership | | | | | | | | ● |
| Full-stack engineering & UX | ◐ | | | | | | | ● |
| Stakeholder communication | ◐ | ● | ◐ | ◐ | ● | ● | ◐ | ● |
| Travel / on-site deployment | | ◐ | | | ◐ | ● | | |

## Field guide entries

### Family: Foundation-model application engineering

**AI Engineer** — Established. Seen at startups to enterprise; fastest-growing
title on LinkedIn.

Builds products on top of pre-trained foundation models rather than training
models from scratch. Coined by Shawn "swyx" Wang's 2023 essay "The Rise of
the AI Engineer," the title centers on RAG pipelines, agent and tool-calling
orchestration, prompt design, and evaluation of LLM outputs running in
production.

- *Core responsibilities:* design/maintain RAG pipelines (chunking,
  embeddings, vector stores, retrieval, reranking); integrate LLM provider
  APIs into product features; build and orchestrate multi-step agent
  workflows; design and run evals (incl. LLM-as-judge) for production
  quality; write production backend/API code around AI features; manage
  prompt/context design plus cost and latency; build observability for AI
  features (tracing, cost, latency).
- *Core skills:* Python (often + TypeScript); RAG architecture and vector
  databases; LLM API integration and function/tool calling; agent frameworks
  (LangGraph, CrewAI) and light orchestration; prompt engineering and context
  design; eval design and production observability; production software
  engineering at scale.
- *Field marks:* distinguished from Machine Learning Engineer by what it
  doesn't do — no training loop, no feature engineering pipeline from raw
  data. It's the umbrella title that Applied AI Engineer, Agentic Engineer,
  and Founding AI Engineer are each a specialization of.
- Sources: [Latent.Space, The Rise of the AI Engineer](https://www.latent.space/p/ai-engineer) ·
  [Humanloop, What is an AI Engineer?](https://humanloop.com/blog/what-is-an-AI-Engineer) ·
  [BLEN, AI Engineer posting](https://jobs.lever.co/blencorp/4b2e3689-9720-4785-b0fe-d09bd5325f74)

**Applied AI Engineer** — Established. Seen at Anthropic, Ramp, Zapier,
DevRev, Cognition.

A hybrid of software engineer and solutions architect. At Anthropic, where
the title is most visible, it's closer to a customer-facing, forward-deployed
role: helping external customers integrate the company's own models into
their products, from discovery through production. At more product-native
companies it skews closer to internal engineering: fine-tuning, workflow
automation, retrieval tuning.

- *Core responsibilities:* act as technical advisor across a customer's
  deployment lifecycle; translate business needs into technical
  implementations with sales/solutions teams; shape architecture through
  pilots, prototypes, evaluation frameworks; run hands-on technical workshops
  and code reviews with customer teams; document emerging LLM usage patterns
  for internal product teams; build agentic workflows and tune retrieval for
  customer-specific data.
- *Core skills:* production LLM experience (advanced prompting, agent
  development, eval methodology); strong Python or TypeScript;
  customer-facing communication, cross-functional collaboration; comfort
  translating ambiguous business requirements into architecture; vector
  databases, embeddings, semantic search tuning; fine-tuning foundation
  models on proprietary data.
- *Field marks:* sits between AI Engineer and Forward Deployed Engineer.
  Where AI Engineer builds internal product features, Applied AI Engineer
  leans toward advising external teams on how to use the company's own
  models.
- Sources: [Anthropic, Applied AI Engineer, Enterprise Tech](https://job-boards.greenhouse.io/anthropic/jobs/5057647008) ·
  [Zapier, Engineer, Applied AI](https://jobs.ashbyhq.com/zapier/38434b88-086c-424b-8d18-8d006e0b71b8)

**Agentic Engineer** — Emerging. Seen at Exelixis, Lightspeed Commerce,
Deloitte, KPMG.

Designs, builds, and operates software agents that plan, call tools, and take
multi-step autonomous actions toward a goal, rather than producing
single-shot model output. US postings mentioning "agentic systems" went from
151 in 2024 to over 16,500 in 2025.

- *Core responsibilities:* design multi-agent workflows and orchestration;
  implement tool-use and planning/execution reasoning loops; build
  short/long-term memory architectures for agents; build eval pipelines and
  traces to catch wrong/inconsistent output; design guardrails, permissions,
  retry paths, human-in-the-loop review; evolve rapid "vibe-coded" prototypes
  into tested, modular production code; monitor and maintain agents once
  live, not just in demos.
- *Core skills:* agent orchestration frameworks (LangGraph, CrewAI, AutoGen,
  Claude Agent SDK); Model Context Protocol (MCP) and tool/function-calling
  design; prompt engineering with structured prompt/version management;
  Python and/or TypeScript; REST API integration and automated testing;
  evals designed for multi-turn, agentic workflows specifically; AI-native
  coding tools (Claude Code, GitHub Copilot).
- *Field marks:* treats orchestration, tool-use design, and multi-agent
  evals as the center of the job, where AI Engineer treats agents as one
  feature among several. Rarely trains models, unlike Machine Learning
  Engineer; treats prompting as one input into a larger system rather than
  the whole task.
- Sources: [Exelixis, AI and Agentic Engineer I](https://www.linkedin.com/jobs/view/ai-and-agentic-engineer-i-at-exelixis-4450381696) ·
  [Lyzr, What Is an Agent Engineer?](https://www.lyzr.ai/blog/what-is-an-agent-engineer/)

**AI Product Engineer / Founding AI Engineer** — Established at startups.
Seen at PostHog, and YC seed-stage startups.

A full-stack generalist who owns a product area end to end, integrating AI as
part of that ownership rather than as the entire job. "AI Product Engineer"
(PostHog's usage) implies an existing product and design system to build
within; "Founding AI Engineer" (common at pre-seed/seed YC startups) implies
building the foundational system from zero, with higher equity and
ambiguity.

- *Core responsibilities:* own a feature/product area end to end (idea,
  build, ship, iterate with users); integrate LLM APIs and agentic features
  as part of a broader product surface; design evaluation and observability
  for AI-driven features; talk to users directly and iterate on feedback;
  ship and own basic UX, not just backend/AI plumbing; at founding stage, set
  architecture and technical direction with no existing scaffolding.
- *Core skills:* full-stack engineering (frontend and backend, not just
  AI/ML plumbing); LLM API integration and basic RAG/agent work; product
  sense (evaluating what to build, not only how); comfort with high
  ambiguity and ownership; direct user/customer communication; pricing and
  business-outcome awareness; rapid MVP iteration and shipping discipline.
- *Field marks:* AI/LLM work is a slice of the job, not the whole job
  (unlike AI Engineer). Builds the company's own product rather than
  advising outside customers (unlike Applied AI/FDE). Compensation at
  founding stage runs $150K–$280K salary plus 0.25%–2.5% equity.
- Sources: [PostHog, AI Product Engineer](https://posthog.com/careers/ai-product-engineer) ·
  [Y Combinator, Founding Engineer postings](https://www.ycombinator.com/companies/primitive/jobs/BN1qxqc-founding-engineer)

### Family: Model & infrastructure engineering

**Machine Learning Engineer** — Established. Seen at every company with a
data science function.

Builds and trains models from data: the full pipeline from data collection
and feature engineering through model training, evaluation, and production
deployment. The title still centers on building and training models, though
many 2025–2026 postings now also expect fluency in fine-tuning and serving
foundation models alongside classic ML work.

- *Core responsibilities:* collect/clean/preprocess data, design feature
  engineering pipelines; select, train, evaluate ML/deep learning
  algorithms; hyperparameter tuning and error analysis; build/maintain
  training pipelines for reproducible results; deploy trained models to
  production and monitor performance drift; automate retraining and testing;
  increasingly, fine-tune foundation models and build RAG pipelines where
  relevant.
- *Core skills:* Python plus SQL (Java/C++ at some companies); ML
  frameworks (PyTorch, TensorFlow, scikit-learn); feature engineering and
  data pipeline design; model training, fine-tuning, hyperparameter tuning;
  statistics, probability, algorithms; deployment basics (containers, cloud
  ML services); growing expectation of RAG and vector databases where the
  product is LLM-adjacent.
- *Field marks:* the training loop is the tell — ML Engineer owns the model
  artifact from raw data through a trained model, where AI Engineer consumes
  a pre-trained model via API. Distinguished from MLOps Engineer by
  ownership: MLE builds the model, MLOps runs it reliably once built.
- Sources: [LinkedIn, ML Engineer hiring guide](https://business.linkedin.com/hire/resources/how-to-hire-guides/machine-learning-engineer-job-description) ·
  [Toptal, ML Engineer job description](https://www.toptal.com/machine-learning/job-description)

**MLOps Engineer** — Established. Seen at Experian, General Dynamics, and
most mid-to-large ML orgs.

Bridges data scientists, ML engineers, and platform teams. Owns the
deployment, monitoring, scaling, and reliability of ML models already in or
headed toward production, rather than building the models themselves.

- *Core responsibilities:* build/maintain MLOps pipelines (training,
  validation, deployment, monitoring); implement CI/CD and
  infrastructure-as-code for ML releases; containerize and orchestrate
  serving infrastructure; monitor model performance and data/model drift,
  automate retraining and alerting; manage model versioning, artifact
  tracking, reproducibility; manage compute cost and scaling for inference;
  collaborate with data scientists/ML engineers to productionize their work.
- *Core skills:* Python (sometimes Java/Scala); DevOps and CI/CD tooling;
  Docker, Kubernetes; cloud ML platforms (SageMaker, Vertex AI, Azure ML);
  infrastructure-as-code (Terraform, CloudFormation); experiment tracking
  (MLflow, Kubeflow, Weights & Biases); model monitoring, drift detection,
  workflow orchestration.
- *Field marks:* per Coursera, "ML engineers focus more on bringing
  individual projects to production, while MLOps engineers work more on
  building a platform" that ML engineers and data scientists use. Differs
  from plain DevOps Engineer by tracking data and models in addition to
  code, and by handling probabilistic systems that degrade silently in ways
  standard unit tests don't catch. Notably: **no RAG or vector-database
  requirement** — this title is about operating already-built models, not
  building them.
- Sources: [Experian, MLOps Engineer](https://jobs.experian.com/job/mlops-engineer-machine-learning-engineer-remote-in-united-states-jid-3846) ·
  [Coursera, MLOps Engineer: Roles, Skills, Career Path](https://www.coursera.org/articles/mlops-engineer)

### Family: Customer-facing delivery

**AI Solutions Architect** — Established. Seen at Deloitte, Accenture, cloud
and enterprise vendors.

Designs and scopes enterprise AI systems for clients, translating business
requirements into technical architecture on a specific cloud stack. Design-
and pre-sales-oriented: makes architecture and feasibility decisions, then
largely hands off the build to a delivery team.

- *Core responsibilities:* analyze client business needs and translate them
  into AI system architecture; design end-to-end GenAI solutions from
  concept to production handoff; select and architect across a cloud stack
  (Azure OpenAI, AWS, GCP); define integration patterns with existing
  enterprise systems; assess technical feasibility, cost, scalability
  trade-offs; guide delivery teams rather than build the whole system solo;
  support pre-sales (scoping, proposals, proof-of-concept design).
- *Core skills:* cloud platform architecture (Azure, AWS, or GCP AI
  services); LLM, RAG, and agent-orchestration system design; enterprise
  systems integration (APIs, data platforms, security); client-facing
  communication and requirements gathering; solution and technical
  leadership; cost, scalability, feasibility analysis; lighter,
  proof-of-concept-level coding rather than production builds.
- *Field marks:* the coding-time split tells the story — Solutions
  Architects report spending roughly 20% or less of their time in an IDE,
  against a Forward Deployed Engineer's up to 70%. Solutions Architect owns
  the design/feasibility call before a system ships; FDE owns the system
  after it ships.
- Sources: [Deloitte, AI Solutions Architect](https://careers.deloitte.ca/job/AI-Solutions-Architect/132266-en_US/) ·
  [Exponent, FDE vs. Solutions Architect](https://www.tryexponent.com/blog/forward-deployed-engineer-vs-solutions-architect)

**Forward Deployed Engineer** — Expanding fast. Origin: Palantir; now at
OpenAI, Anthropic, Google Cloud.

Embeds directly with a customer's team, on-site or close to it, to rapidly
build, customize, and ship production AI applications on the customer's own
infrastructure and data. Owns the deployed system after it ships. Postings
grew roughly 800% between April 2025 and 2026 as OpenAI, Anthropic, and
Google Cloud adopted the title.

- *Core responsibilities:* embed on-site or closely with customer
  engineering/business teams; rapidly prototype and build production-grade
  applications on customer infrastructure; customize models, agents, and
  tools to the customer's data and workflows; deliver concrete artifacts
  (integrations, MCP servers, sub-agents, custom pipelines); provide
  hands-on, "white-glove" deployment and troubleshooting support; feed
  repeatable deployment patterns back to core product teams; maintain the
  customer relationship across the full engagement.
- *Core skills:* production-grade software engineering (Python primary,
  TypeScript/Java common); rapid prototyping under real-world constraints;
  client-facing communication and relationship management; prompt
  engineering and agent development experience; enterprise systems
  integration inside a customer's existing stack; comfort with ambiguity and
  autonomous problem-solving; frequent travel (25%–50% typical).
- *Field marks:* heavy hands-on coding (up to ~70% of time) plus ownership
  of the system after go-live separates FDE from Solutions Architect's
  lighter, pre-sales-focused build. Overlaps closely with Applied AI
  Engineer — at Anthropic the two cover largely the same work, with FDE the
  primary label at OpenAI and Palantir.
- Sources: [Anthropic, Forward Deployed Engineer](https://job-boards.greenhouse.io/anthropic/jobs/5302966008) ·
  [MarkTechPost, What Is a Forward Deployed Engineer?](https://www.marktechpost.com/2026/05/20/what-is-a-forward-deployed-engineer-the-ai-role-openai-anthropic-and-google-are-hiring-in-2026/)

## Cross-cutting skillset

Appears as a named expectation across most of the eight titles, regardless of
specialization:

1. **Python** as the working language of the field
2. **Working with foundation-model / LLM APIs** rather than only classic ML libraries
3. **Prompt and context literacy**, even where "Prompt Engineer" as a title has faded
4. **Evaluating AI output**: building evals, catching hallucination, drift, and regressions
5. **Shipping to production**, not stopping at a notebook or a demo
6. **Cloud infrastructure literacy** across AWS, GCP, or Azure
7. **Stakeholder communication**: translating technical work for business, product, or customer audiences
8. **RAG and retrieval fundamentals**: embeddings, vector search, grounding

## What actually differentiates titles

The specific skill that, more than any other, marks a candidate as one title
rather than another:

- **Training or fine-tuning models from scratch** — separates Machine
  Learning Engineer from every API-consuming title
- **Multi-agent orchestration and tool-use design** — the specialization that
  defines Agentic Engineer
- **CI/CD, containers, and drift monitoring as the whole job** — the
  specialization that defines MLOps Engineer
- **Pre-sales scoping with light coding, ~20% IDE time** — defines AI
  Solutions Architect, against FDE's ~70%
- **Customer embedding, travel, and post-ship ownership** — defines Forward
  Deployed Engineer
- **Product ownership, pricing, UX, support rotation** — defines AI Product /
  Founding AI Engineer
