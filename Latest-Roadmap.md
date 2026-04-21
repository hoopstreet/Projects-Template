MAID Protocol — Production-Grade Complete Roadmap.md

🧬 Project Identity: TikTok-Prompt-Generator DNA

Lead Developer: hoopstreet
Email: hoopstreet143@gmail.com
GitHub: hoopstreet
Environment: iSH (Alpine Linux) on iPhone
Architecture: Zero-Local-Load (ZLL) + Production-Grade DevOps

---

📖 Table of Contents

1. Architecture Overview
2. The Two-File System
3. Developer Roles
4. Table Structures
5. Human Coder — Complete Examples & Templates
6. AI Provider Training Guide
7. Human Coder — Strict Rules
8. iSH Implementation Scripts
9. Quick Reference Card
10. Next 10 Development Suggestions
11. AI Self-Coder — Multi-Model Setup
12. AI Self-Coder — Complete Examples & Behaviors
13. Production-Grade Workflow Stack
14. Complete Workflow Cycle
15. Error Recovery Protocol
16. Status Legend
17. Current Status Dashboard

---

1. Architecture Overview

Production-Grade Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────────────────────────────────────────┐
│                         MAID PROTOCOL — PRODUCTION-GRADE ARCHITECTURE                                │
├─────────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                                      │
│  ┌─────────────────────────────────────────────────────────────────────────────────────────────┐   │
│  │                              HUMAN CODER (iPhone iSH)                                         │   │
│  │                                                                                               │   │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐                     │   │
│  │  │   ChatGPT    │  │   Gemini     │  │  Deepseek    │  │   Claude     │                     │   │
│  │  └──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘                     │   │
│  │         │                 │                 │                 │                              │   │
│  │         └─────────────────┴─────────────────┴─────────────────┘                              │   │
│  │                                            │                                                  │   │
│  │                              Generate cat << 'EOF' scripts                                    │   │
│  │                                            │                                                  │   │
│  │                            ┌───────────────┴───────────────┐                                  │   │
│  │                            │   Task.md + Roadmap.md        │                                  │   │
│  │                            │   (with 'new' status)         │                                  │   │
│  │                            └───────────────┬───────────────┘                                  │   │
│  │                                            │                                                  │   │
│  │                                   git push (execute: roadmap)                                │   │
│  └────────────────────────────────────────────┼─────────────────────────────────────────────────┘   │
│                                               │                                                     │
│                                               ▼                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────────────────────┐   │
│  │                              VALIDATION LAYER (maid-ci.yml)                                  │   │
│  │                                                                                               │   │
│  │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────────────┐ │   │
│  │  │  Validate YAML  │→ │  Validate Task  │→ │  Check Secrets  │→ │  Lint Python           │ │   │
│  │  └─────────────────┘  └─────────────────┘  └─────────────────┘  └─────────────────────────┘ │   │
│  └────────────────────────────────────────────┼────────────────────────────────────────────────┘   │
│                                               │                                                     │
│                                               ▼                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────────────────────┐   │
│  │                              SECURITY LAYER (maid-security.yml)                              │   │
│  │                                                                                               │   │
│  │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────────────┐ │   │
│  │  │  Secret Scan    │→ │  Trivy Scan     │→ │  Dependency     │→ │  Token Validation       │ │   │
│  │  └─────────────────┘  └─────────────────┘  └─────────────────┘  └─────────────────────────┘ │   │
│  └────────────────────────────────────────────┼────────────────────────────────────────────────┘   │
│                                               │                                                     │
│                                               ▼                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────────────────────┐   │
│  │                              AI EXECUTION LAYER (maid-executor.yml)                          │   │
│  │                                                                                               │   │
│  │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────────────┐ │   │
│  │  │  Task Scanner   │→ │  Model Router   │→ │  AI Executor    │→ │  Status Update          │ │   │
│  │  └─────────────────┘  └─────────────────┘  └─────────────────┘  └─────────────────────────┘ │   │
│  │                                                                                               │   │
│  │  Priority Models: DeepSeek-V3 → Qwen2.5 → Llama-3.3 → StarCoder2 → Gemini Backup            │   │
│  └────────────────────────────────────────────┼────────────────────────────────────────────────┘   │
│                                               │                                                     │
│                                               ▼                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────────────────────┐   │
│  │                              DEPLOYMENT PIPELINE                                             │   │
│  │                                                                                               │   │
│  │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────────────┐ │   │
│  │  │  docker-build   │→ │  docker-push    │→ │  hf-sync        │→ │  Version Sync Engine    │ │   │
│  │  └─────────────────┘  └─────────────────┘  └─────────────────┘  └─────────────────────────┘ │   │
│  └────────────────────────────────────────────┼────────────────────────────────────────────────┘   │
│                                               │                                                     │
│                                               ▼                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────────────────────┐   │
│  │                              BACKGROUND SERVICES                                             │   │
│  │                                                                                               │   │
│  │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────────────┐ │   │
│  │  │ maid-scheduler  │  │ maid-retry      │  │ maid-monitor    │  │ maid-issue-bot          │ │   │
│  │  │ (every 15 min)  │  │ (failure recov) │  │ (health check)  │  │ (auto-issues)           │ │   │
│  │  └─────────────────┘  └─────────────────┘  └─────────────────┘  └─────────────────────────┘ │   │
│  │                                                                                               │   │
│  │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────────────┐ │   │
│  │  │ maid-release    │  │ maid-rollback   │  │ maid-cleanup    │  │ maid-env-check          │ │   │
│  │  │ (version/tag)   │  │ (disaster rec)  │  │ (artifact clean)│  │ (credential check)      │ │   │
│  │  └─────────────────┘  └─────────────────┘  └─────────────────┘  └─────────────────────────┘ │   │
│  └─────────────────────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                                      │
│  RESULT: ✅ GitHub → Docker Hub → Hugging Face — ALL VERSIONS MATCH                                 │
│                                                                                                      │
└─────────────────────────────────────────────────────────────────────────────────────────────────────┘
```

Version Sync Authority Flow

```
┌─────────────────────────────────────────────────────────────────────────────────────────────────────┐
│                              VERSION SYNC AUTHORITY PIPELINE                                          │
├─────────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                                      │
│  ┌─────────────────────────────────────────────────────────────────────────────────────────────┐   │
│  │  STEP 1: Source Change Detector                                                               │   │
│  │                                                                                               │   │
│  │  Trigger: Push to main OR scheduled OR manual                                                │   │
│  │  Action: Detect changes in Task.md, Roadmap.md, .py, .yml, Dockerfile                        │   │
│  └─────────────────────────────────────────────────────────────────────────────────────────────┘   │
│                                               │                                                     │
│                                               ▼                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────────────────────┐   │
│  │  STEP 2: Version Authority (Decides vX.X.X)                                                  │   │
│  │                                                                                               │   │
│  │  Rules:                                                                                       │   │
│  │  - Human Coder → Minor bump (v1.2.0 → v1.3.0)                                                │   │
│  │  - AI Self-Coder → Patch bump (v1.3.0 → v1.3.1)                                              │   │
│  │  - Major change detected → Major bump (v1.9.9 → v2.0.0)                                      │   │
│  └─────────────────────────────────────────────────────────────────────────────────────────────┘   │
│                                               │                                                     │
│                                               ▼                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────────────────────┐   │
│  │  STEP 3: Docker Build & Push                                                                 │   │
│  │                                                                                               │   │
│  │  - Build: docker build -t hoopstreet/tiktok-prompt-generator:vX.X.X .                        │   │
│  │  - Push: docker push hoopstreet/tiktok-prompt-generator:vX.X.X                               │   │
│  │  - Tag latest: docker tag ... latest && docker push ... latest                               │   │
│  └─────────────────────────────────────────────────────────────────────────────────────────────┘   │
│                                               │                                                     │
│                                      (ONLY IF SUCCESS)                                              │
│                                               ▼                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────────────────────┐   │
│  │  STEP 4: Version Sync Engine                                                                  │   │
│  │                                                                                               │   │
│  │  - Update hf.Dockerfile with matching tag                                                    │   │
│  │  - Commit: "ai: update hf.Dockerfile to vX.X.X"                                              │   │
│  │  - Push to GitHub                                                                             │   │
│  └─────────────────────────────────────────────────────────────────────────────────────────────┘   │
│                                               │                                                     │
│                                               ▼                                                     │
│  ┌─────────────────────────────────────────────────────────────────────────────────────────────┐   │
│  │  STEP 5: Hugging Face Sync                                                                    │   │
│  │                                                                                               │   │
│  │  - Clone HF Space                                                                             │   │
│  │  - Copy Dockerfile and README.md                                                              │   │
│  │  - Push to HF Space                                                                           │   │
│  │  - Space auto-rebuilds with new image                                                         │   │
│  └─────────────────────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                                      │
│  FINAL RESULT (ALL VERSIONS MATCH):                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────────────────────────┐   │
│  │  GitHub Tag:        v1.2.3                                                                    │   │
│  │  Docker Hub:        hoopstreet/tiktok-prompt-generator:v1.2.3                                │   │
│  │  hf.Dockerfile:     FROM hoopstreet/tiktok-prompt-generator:v1.2.3                           │   │
│  │  Hugging Face Space: Running v1.2.3                                                          │   │
│  └─────────────────────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                                      │
└─────────────────────────────────────────────────────────────────────────────────────────────────────┘
```

---

2. The Two-File System

```
~/TikTok-Prompt-Generator/
├── Task.md                    ← Human input buffer (Kanban/Sheets style)
├── Roadmap.md                 ← AI output reality (Story/Documentation style)
├── CHANGELOG.md               ← Auto-generated by AI Self-Coder
├── .github/
│   ├── workflows/
│   │   ├── maid-ci.yml        ← PRE-EXECUTION VALIDATOR ⚠️ CRITICAL
│   │   ├── maid-security.yml  ← SECURITY & VULNERABILITY SCAN ⚠️ CRITICAL
│   │   ├── maid-executor.yml  ← AI BRAIN (EXISTS)
│   │   ├── maid-scheduler.yml ← AUTONOMOUS RUNNER (every 15 min) ⚠️ CRITICAL
│   │   ├── maid-retry-engine.yml ← FAILURE RECOVERY ⚠️ CRITICAL
│   │   ├── maid-pr-agent.yml  ← CODE REVIEW AI
│   │   ├── maid-release.yml   ← VERSION & RELEASE MANAGER ⚠️ CRITICAL
│   │   ├── maid-rollback.yml  ← DISASTER RECOVERY ⚠️ CRITICAL
│   │   ├── maid-monitor.yml   ← HEALTH MONITORING
│   │   ├── maid-issue-bot.yml ← AUTO ISSUE CREATOR
│   │   ├── docker-build.yml   ← BUILD IMAGE ONLY
│   │   ├── docker-push.yml    ← PUSH TO DOCKER HUB
│   │   ├── hf-sync.yml        ← SYNC TO HUGGING FACE
│   │   ├── maid-test.yml      ← UNIT & INTEGRATION TESTS
│   │   ├── maid-lint.yml      ← CODE STYLE ENFORCEMENT
│   │   ├── maid-env-check.yml ← CREDENTIAL VALIDATION
│   │   └── maid-cleanup.yml   ← ARTIFACT CLEANUP
│   └── backups/               ← Original version backups
└── ...

```

File Purposes

File Owner Purpose Criticality
Task.md Human Coder Input Buffer — The "What" ✅ REQUIRED
Roadmap.md AI Self-Coder Output Reality — The "How" ✅ REQUIRED
maid-ci.yml AI Self-Coder Pre-execution validator 🔴 CRITICAL
maid-security.yml AI Self-Coder Secrets & vulnerability scan 🔴 CRITICAL
maid-scheduler.yml AI Self-Coder Autonomous runner (every 15 min) 🔴 CRITICAL
maid-retry-engine.yml AI Self-Coder Failure recovery system 🔴 CRITICAL
maid-release.yml AI Self-Coder Version & release manager 🔴 CRITICAL
maid-rollback.yml AI Self-Coder Disaster recovery 🔴 CRITICAL
maid-executor.yml AI Self-Coder AI brain (exists) ✅ REQUIRED
maid-monitor.yml AI Self-Coder Health monitoring 🟡 HIGH VALUE
maid-issue-bot.yml AI Self-Coder Auto issue creator 🟡 HIGH VALUE
maid-pr-agent.yml AI Self-Coder Code review AI 🟢 OPTIONAL
docker-build.yml AI Self-Coder Build image only ✅ REQUIRED
docker-push.yml AI Self-Coder Push to Docker Hub ✅ REQUIRED
hf-sync.yml AI Self-Coder Sync to Hugging Face ✅ REQUIRED
maid-test.yml AI Self-Coder Unit & integration tests 🟡 HIGH VALUE
maid-lint.yml AI Self-Coder Code style enforcement 🟢 OPTIONAL
maid-env-check.yml AI Self-Coder Credential validation 🟡 HIGH VALUE
maid-cleanup.yml AI Self-Coder Artifact cleanup 🟢 OPTIONAL

---

3. Developer Roles

Role 1: Human Coder (Commander) — Priority FIRST

Aspect Details
Priority FIRST — Establishes the entire foundation
Device iPhone running iSH (Alpine Linux)
AI Code Providers ChatGPT, Gemini, Deepseek, Claude
Code Rules STRICT — 150-char limit, cat EOF only, no nano/vi
Primary Action Deploy templated Task.md and Roadmap.md
Primary Mission Build ALL 17 production-grade workflows
Commit Style execute: roadmap vX.X.X
Credentials GitHub Secrets + local credential.helper store
Never Does Manual edits with nano/vi, edits Roadmap.md directly

Role 2: AI Self-Coder (Executor) — 247 Active Production-Grade

Aspect Details
Priority SECOND — Activated after Human pushes
Environment GitHub Actions Runner (cloud)
Primary Mission Run production-grade workflow stack
Workflows 17 modular workflows (validation → security → execution → deployment)
Models DeepSeek-V3, Qwen2.5-Coder, Llama-3.3, StarCoder2, Gemini
Auto-Scaling Scheduled every 15 minutes (not just push-based)
Error Handling Dedicated retry engine + rollback system
Observability Health monitoring + auto-issue bot
Security Secret scanning + vulnerability detection

---

4. Table Structures

Task.md — Kanban/Sheets Style (Input)

# Task Description Notes Tags Status Dev
1 iSH Environment Setup Alpine Linux configuration git init, credential store v0.1.0 stable ✅ Human Coder
2 GitHub Auth Setup PAT and remote connection credential.helper store v0.1.0 setup ✅ Human Coder
3 GitHub Secrets Config Store tokens securely HF_TOKEN, GEMINI_API_KEY v0.1.5 security ✅ Human Coder
4 AI Self-Coder Developer Create base workflow maid-executor.yml v0.2.0 automation new Human Coder
5 AI Self-Coder Multi-Model Integrate HF + Gemini models DeepSeek, Qwen, Llama, StarCoder v0.3.0 feature new Human Coder
6 CI Validator Create maid-ci.yml Pre-execution validation v0.4.0 ci new Human Coder
7 Security Scanner Create maid-security.yml Secrets & vulnerability scan v0.4.1 security new Human Coder
8 Scheduler Create maid-scheduler.yml Run every 15 minutes v0.4.2 automation new Human Coder
9 Retry Engine Create maid-retry-engine.yml Failure recovery v0.4.3 reliability new Human Coder
10 Release Manager Create maid-release.yml Version & tag management v0.4.4 release new Human Coder
11 Rollback System Create maid-rollback.yml Disaster recovery v0.4.5 recovery new Human Coder
12 Monitor & Issue Bot Create maid-monitor.yml + maid-issue-bot.yml Observability v0.5.0 monitoring 📅 AI Self-Coder
13 Docker Pipeline Split docker-build.yml + docker-push.yml + hf-sync.yml Deployment v0.6.0 deployment 📅 AI Self-Coder
14 Testing & Lint Create maid-test.yml + maid-lint.yml Quality v0.7.0 quality 📅 AI Self-Coder
15 Business Logic Setup TikTok Prompt Generator Core product development v1.0.0 feature 📅 AI Self-Coder

Roadmap.md — Story/Documentation Style (Output)

Section 1: Foundation (v0.1.0) — ✅ COMPLETED

Initial setup and infrastructure.

Milestone Description Status
iSH Environment Alpine Linux configured on iPhone ✅
GitHub Connection Remote origin with credential persistence ✅
Secrets Management HF_TOKEN, GEMINI_API_KEY configured ✅

Section 2: AI Self-Coder Developer (v0.2.0) — 🔄 IN PROGRESS

Building the core AI Self-Coder workflow.

Milestone Description Status
Base Workflow maid-executor.yml created ⌛
Multi-Model DeepSeek, Qwen, Llama, StarCoder, Gemini ⌛

Section 3: Production-Grade Workflow Stack (v0.4.0) — 🔄 IN PROGRESS

Building the complete professional DevOps pipeline.

Priority Workflow Purpose Status
🔴 CRITICAL maid-ci.yml Pre-execution validator new
🔴 CRITICAL maid-security.yml Secrets & vulnerability scan new
🔴 CRITICAL maid-scheduler.yml Autonomous runner (every 15 min) new
🔴 CRITICAL maid-retry-engine.yml Failure recovery new
🔴 CRITICAL maid-release.yml Version & release manager new
🔴 CRITICAL maid-rollback.yml Disaster recovery new
🟡 HIGH maid-monitor.yml Health monitoring 📅
🟡 HIGH maid-issue-bot.yml Auto issue creator 📅
🟢 OPTIONAL maid-pr-agent.yml Code review AI 📅
🟡 HIGH maid-test.yml Unit & integration tests 📅
🟢 OPTIONAL maid-lint.yml Code style enforcement 📅
🟡 HIGH maid-env-check.yml Credential validation 📅
🟢 OPTIONAL maid-cleanup.yml Artifact cleanup 📅

Section 4: Deployment Pipeline (v0.6.0) — 📅 PLANNED

Split deployment pipeline for reliability.

Milestone Description Status
docker-build.yml Build image only 📅
docker-push.yml Push to Docker Hub 📅
hf-sync.yml Sync to Hugging Face 📅
Version Sync Engine Auto-match all versions 📅

Section 5: Business Logic (v1.0.0) — 📅 READY

Core product development after AI Self-Coder is complete.

Milestone Description Status
TikTok Prompt Engine AI script generation 📅
Video Pipeline ElevenLabs + Creatomate 📅
Production Full deployment 📅

---

5. Human Coder — Complete Examples & Templates

Template 1: Pre-Templated Task.md (Complete List with Production Workflows)

```bash
cd ~/TikTok-Prompt-Generator || exit

cat << 'EOF' > Task.md
# 🛠 Task Ledger: TikTok-Prompt-Generator
| # | Task | Description | Notes | Tags | Status | Dev |
|:---|:---|:---|:---|:---|:---|:---|
| 1 | iSH Environment Setup | Alpine Linux configuration | git init, credential store | v0.1.0 stable | ✅ | Human Coder |
| 2 | GitHub Auth Setup | PAT and remote connection | credential.helper store | v0.1.0 setup | ✅ | Human Coder |
| 3 | GitHub Secrets Config | Store tokens securely | HF_TOKEN, GEMINI_API_KEY | v0.1.5 security | ✅ | Human Coder |
| 4 | AI Self-Coder Developer | Create base workflow | maid-executor.yml | v0.2.0 automation | new | Human Coder |
| 5 | AI Self-Coder Multi-Model | Integrate HF + Gemini models | DeepSeek, Qwen, Llama, StarCoder | v0.3.0 feature | new | Human Coder |
| 6 | CI Validator | Create maid-ci.yml | Pre-execution validation | v0.4.0 ci | new | Human Coder |
| 7 | Security Scanner | Create maid-security.yml | Secrets & vulnerability scan | v0.4.1 security | new | Human Coder |
| 8 | Scheduler | Create maid-scheduler.yml | Run every 15 minutes | v0.4.2 automation | new | Human Coder |
| 9 | Retry Engine | Create maid-retry-engine.yml | Failure recovery | v0.4.3 reliability | new | Human Coder |
| 10 | Release Manager | Create maid-release.yml | Version & tag management | v0.4.4 release | new | Human Coder |
| 11 | Rollback System | Create maid-rollback.yml | Disaster recovery | v0.4.5 recovery | new | Human Coder |
| 12 | Monitor & Issue Bot | Create maid-monitor.yml + maid-issue-bot.yml | Observability | v0.5.0 monitoring | 📅 | AI Self-Coder |
| 13 | Docker Pipeline | Split docker-build.yml + docker-push.yml + hf-sync.yml | Deployment | v0.6.0 deployment | 📅 | AI Self-Coder |
| 14 | Testing & Lint | Create maid-test.yml + maid-lint.yml | Quality | v0.7.0 quality | 📅 | AI Self-Coder |
| 15 | Business Logic Setup | TikTok Prompt Generator | Core product development | v1.0.0 feature | 📅 | AI Self-Coder |
EOF

# BLANK LINE AFTER EOF
```

Template 2: Pre-Templated Roadmap.md (Production-Grade)

```bash
cat << 'EOF' > Roadmap.md
# 🗺 Project Roadmap: TikTok-Prompt-Generator

## Section 1: Foundation (v0.1.0) — ✅ COMPLETED

### Updating from initial setup
- **1.1** iSH Environment: Alpine Linux configured on iPhone
- **1.2** GitHub Connection: Remote origin with credential persistence
- **1.3** Secrets Management: HF_TOKEN, GEMINI_API_KEY configured

---

## Section 2: AI Self-Coder Developer (v0.2.0) — 🔄 IN PROGRESS

### Building from new development
- **2.1** Base Workflow: maid-executor.yml created
- **2.2** Multi-Model: DeepSeek, Qwen, Llama, StarCoder, Gemini

---

## Section 3: Production-Grade Workflow Stack (v0.4.0) — 🔄 IN PROGRESS

### 🔴 CRITICAL WORKFLOWS (Must Build First)

#### 3.1 maid-ci.yml — Pre-Execution Validator
- Validate YAML syntax
- Validate Task.md format
- Check secrets existence
- Lint Python code
- Prevent broken pushes before AI execution

#### 3.2 maid-security.yml — Security & Vulnerability Scan
- Detect exposed tokens (HF_TOKEN, GEMINI_API_KEY)
- Scan dependencies with Trivy
- Prevent secret leaks
- GitHub Advanced Security integration

#### 3.3 maid-scheduler.yml — Autonomous Runner
- Run every 15 minutes (cron: "*/15 * * * *")
- 24/7 operation (not just push-based)
- Auto-detect and execute pending tasks

#### 3.4 maid-retry-engine.yml — Failure Recovery
- Handle stuck tasks
- Retry failed workflows
- Reset "Need Human" optionally
- System-wide retry (not job-level)

#### 3.5 maid-release.yml — Version & Release Manager
- Tag versions properly
- Generate release notes
- Attach CHANGELOG
- Coordinate version bumps

#### 3.6 maid-rollback.yml — Disaster Recovery
- Restore from .github/backups
- Rollback bad deployment
- Automatic backup before upgrades

### 🟡 HIGH VALUE WORKFLOWS (Second Wave)

#### 3.7 maid-monitor.yml — Health Monitoring
- Check workflow success rates
- Detect failures
- Alert via logs or issues

#### 3.8 maid-issue-bot.yml — Auto Issue Creator
- Create GitHub Issues when:
  - Task fails
  - Secrets missing
  - Docker fails
- Right now errors are silent — this fixes that

### 🟢 OPTIONAL WORKFLOWS (Final Polish)

#### 3.9 maid-pr-agent.yml — Code Review AI
- Auto-review PRs
- Suggest fixes
- Comment like senior dev

#### 3.10 maid-test.yml — Unit & Integration Tests
- Run tests before deployment
- Prevent broken code from reaching production

#### 3.11 maid-lint.yml — Code Style Enforcement
- Prevent messy AI output
- Enforce consistent formatting

#### 3.12 maid-env-check.yml — Credential Validation
- Validate HF_TOKEN
- Validate GEMINI_API_KEY
- Validate Docker credentials

#### 3.13 maid-cleanup.yml — Artifact Cleanup
- Remove old artifacts
- Clean logs
- Optimize repo size

---

## Section 4: Deployment Pipeline (v0.6.0) — 📅 PLANNED

### Split Deployment Pipeline (Separation = easier debugging)

#### 4.1 docker-build.yml
- Build image only
- No push
- Validate Dockerfile

#### 4.2 docker-push.yml
- Push to Docker Hub
- Tag with version
- Push latest tag

#### 4.3 hf-sync.yml
- Sync to Hugging Face Space
- Update hf.Dockerfile
- Match versions automatically

### Version Sync Authority
- GitHub Tag: v1.2.3
- Docker Hub: hoopstreet/tiktok-prompt-generator:v1.2.3
- hf.Dockerfile: FROM hoopstreet/tiktok-prompt-generator:v1.2.3
- Hugging Face Space: Running v1.2.3

---

## Section 5: Business Logic (v1.0.0) — 📅 READY

### Building from new development
- **5.1** TikTok Prompt Engine: AI script generation from product data
- **5.2** Video Pipeline: ElevenLabs voiceover + Creatomate video
- **5.3** Production Deployment: End-to-end ready

EOF

# BLANK LINE AFTER EOF
```

Template 3: Human Coder Deployment Script (Complete)

```bash
# STEP 1: Enter project directory
cd ~/TikTok-Prompt-Generator || exit

# STEP 2: Deploy Task.md (use Template 1)
cat << 'EOF' > Task.md
# [PASTE TEMPLATE 1 CONTENT HERE]
EOF

# BLANK LINE

# STEP 3: Deploy Roadmap.md (use Template 2)
cat << 'EOF' > Roadmap.md
# [PASTE TEMPLATE 2 CONTENT HERE]
EOF

# BLANK LINE

# STEP 4: Create workflows directory
mkdir -p .github/workflows

# STEP 5: Deploy ALL production workflows (from Section 13)
# maid-ci.yml
cat << 'EOF' > .github/workflows/maid-ci.yml
# [PASTE WORKFLOW FROM SECTION 13.1]
EOF

# BLANK LINE

# maid-security.yml
cat << 'EOF' > .github/workflows/maid-security.yml
# [PASTE WORKFLOW FROM SECTION 13.2]
EOF

# BLANK LINE

# maid-scheduler.yml
cat << 'EOF' > .github/workflows/maid-scheduler.yml
# [PASTE WORKFLOW FROM SECTION 13.3]
EOF

# BLANK LINE

# maid-retry-engine.yml
cat << 'EOF' > .github/workflows/maid-retry-engine.yml
# [PASTE WORKFLOW FROM SECTION 13.4]
EOF

# BLANK LINE

# maid-release.yml
cat << 'EOF' > .github/workflows/maid-release.yml
# [PASTE WORKFLOW FROM SECTION 13.5]
EOF

# BLANK LINE

# maid-rollback.yml
cat << 'EOF' > .github/workflows/maid-rollback.yml
# [PASTE WORKFLOW FROM SECTION 13.6]
EOF

# BLANK LINE

# STEP 6: Commit and push to trigger AI Self-Coder
git add .
git commit -m "execute: roadmap v0.4.0 T-006 T-007 T-008 T-009 T-010 T-011 new"
git pull origin main --rebase
git push origin main

# BLANK LINE
```

---

6. AI Provider Training Guide

Universal AI Training Prompt (For Human Coder's AI Providers)

```text
I am a Human Coder using iSH (Alpine Linux) on iPhone.
We are following the MAID Protocol (Mobile-AI Integrated Development).

CODE RULES (STRICT - ONLY FOR HUMAN CODER):
1. ALL code in cat << 'EOF' blocks
2. MAX 150 characters per line — split if longer
3. NEVER use nano/vi — cat EOF scripts only
4. Every block starts: cd ~/TikTok-Prompt-Generator || exit
5. EOF always followed by blank line
6. Never nest cat inside cat
7. Always end with: git pull origin main --rebase && git push

MY CREDENTIALS:
- GitHub: hoopstreet
- Email: hoopstreet143@gmail.com
- Credential Store: git config --global credential.helper store

PROJECT STRUCTURE:
- Task.md: Kanban/Sheets table (7 columns)
- Roadmap.md: Story/Documentation style
- 17 production-grade workflows in .github/workflows/

PRODUCTION WORKFLOWS NEEDED (PRIORITY ORDER):
1. maid-ci.yml — Pre-execution validator
2. maid-security.yml — Security & vulnerability scan
3. maid-scheduler.yml — Autonomous runner (every 15 min)
4. maid-retry-engine.yml — Failure recovery
5. maid-release.yml — Version & release manager
6. maid-rollback.yml — Disaster recovery
7. maid-monitor.yml — Health monitoring
8. maid-issue-bot.yml — Auto issue creator
9. maid-pr-agent.yml — Code review AI
10. docker-build.yml + docker-push.yml + hf-sync.yml

Generate ALL missing workflows in complete YAML format.
Each workflow must be 150-char compliant and ready to paste.
```

---

7. Human Coder — Strict Rules

Rule Description
Rule 1 No manual edits — never use nano/vi
Rule 2 150-character hard limit — split into multiple cat EOF
Rule 3 EOF safety — never nest cat inside cat
Rule 4 Blank space buffer — blank line after every EOF (auto-execute)
Rule 5 Mobile-first — cd ~/TikTok-Prompt-Generator || exit
Rule 6 Safe-pull protocol — pull --rebase before push
Rule 7 Commit signals — execute: roadmap vX.X.X
Rule 8 Credential persistence — credential.helper store
Rule 9 Always navigate to project — every code block starts with cd
Rule 10 Blank line after EOF — for automatic execution when pasting

---

8. iSH Implementation Scripts

Phase 1: Environment Setup

```bash
mkdir -p ~/TikTok-Prompt-Generator
cd ~/TikTok-Prompt-Generator

git config --global user.name "hoopstreet"
git config --global user.email "hoopstreet143@gmail.com"
git config --global credential.helper store

# BLANK LINE
```

Phase 2: GitHub Connection (One Time)

```bash
cd ~/TikTok-Prompt-Generator || exit

git init
git branch -M main
git remote add origin https://github.com/hoopstreet/TikTok-Prompt-Generator.git

# BLANK LINE
```

Phase 3: Deploy All Workflows

```bash
cd ~/TikTok-Prompt-Generator || exit

mkdir -p .github/workflows

# Deploy each workflow from Section 13
# [PASTE EACH WORKFLOW WITH BLANK LINE AFTER]

# BLANK LINE
```

Phase 4: Initial Push

```bash
cd ~/TikTok-Prompt-Generator || exit

git add .
git commit -m "feat: production-grade MAID Protocol setup v0.4.0"
git pull origin main --rebase
git push origin main

# BLANK LINE
```

iSH Profile Aliases

```bash
# Add to ~/.profile
alias gpl='git pull origin main --rebase'
alias gps='git push origin main'
alias gst='git status'
alias gad='git add .'
alias task='cat Task.md'
alias roadmap='cat Roadmap.md'
alias changelog='cat CHANGELOG.md'
alias pending='grep "| new " Task.md'
alias errors='grep "❌" Task.md'
alias complete='grep "✅" Task.md'
alias needhuman='grep "Need Human" Task.md'
alias workflows='ls .github/workflows/'

alias maid-status='
echo "📊 MAID Protocol Status"
echo "========================"
echo "🆕 Pending:  $(grep -c "| new " Task.md 2>/dev/null || echo 0)"
echo "⏳ Running:  $(grep -c "⌛" Task.md 2>/dev/null || echo 0)"
echo "✅ Done:     $(grep -c "✅" Task.md 2>/dev/null || echo 0)"
echo "❌ Errors:   $(grep -c "❌" Task.md 2>/dev/null || echo 0)"
echo "👤 Need Human: $(grep -c "Need Human" Task.md 2>/dev/null || echo 0)"
echo "📁 Workflows: $(ls -1 .github/workflows/ | wc -l) active"
'

# BLANK LINE
```

---

9. Quick Reference Card

Human Coder Commands

```bash
# Daily start
cd ~/TikTok-Prompt-Generator || exit
git pull origin main --rebase

# Check status
maid-status

# Deploy new tasks (use AI provider for cat EOF block)
git add .
git commit -m "execute: roadmap vX.X.X"
git push origin main

# Check results
grep "✅\|❌\|Need Human" Task.md
cat CHANGELOG.md

# Check workflow status
gh run list --limit 10

# BLANK LINE
```

Commit Messages

Scenario Command
Initial setup git commit -m "feat: production MAID Protocol setup v0.4.0"
Add critical workflows git commit -m "execute: roadmap v0.4.0 T-006 T-007 T-008 T-009 T-010 T-011 new"
AI auto-update Auto-generated: ai: executed tasks ✅
Manual fix git commit -m "fix: reset failed task for retry"
Version release git commit -m "release: v1.0.0"

---

10. Next 10 Development Suggestions

# Suggestion Description Priority
01 maid-ci.yml Pre-execution validator 🔴 CRITICAL
02 maid-security.yml Secrets & vulnerability scan 🔴 CRITICAL
03 maid-scheduler.yml Autonomous runner (every 15 min) 🔴 CRITICAL
04 maid-retry-engine.yml Failure recovery system 🔴 CRITICAL
05 maid-release.yml Version & release manager 🔴 CRITICAL
06 maid-rollback.yml Disaster recovery 🔴 CRITICAL
07 maid-monitor.yml Health monitoring 🟡 HIGH VALUE
08 maid-issue-bot.yml Auto issue creator 🟡 HIGH VALUE
09 Split Docker Pipeline docker-build + docker-push + hf-sync 🟡 HIGH VALUE
10 maid-test.yml + maid-lint.yml Quality assurance 🟢 OPTIONAL

---

11. AI Self-Coder — Multi-Model Setup

Model Priority List (Production)

Priority Model Source Token/Key Best For
1 DeepSeek-V3 Hugging Face HF_TOKEN Complex reasoning, debugging
2 Qwen2.5-Coder-32B Hugging Face HF_TOKEN Python, JavaScript, speed
3 Llama-3.3-70B Hugging Face HF_TOKEN Long-form documentation
4 StarCoder2-15B Hugging Face HF_TOKEN Code completion, 600+ languages
5 Gemini API Key GEMINI_API_KEY Backup when HF fails

Required Secrets for Production

Secret Purpose Where to Get Criticality
HF_TOKEN Hugging Face Inference API huggingface.co/settings/tokens 🔴 REQUIRED
GEMINI_API_KEY Google Gemini Backup makersuite.google.com/app/apikey 🟡 RECOMMENDED
DOCKERHUB_USERNAME Docker Hub push hub.docker.com 🔴 REQUIRED
DOCKERHUB_TOKEN Docker Hub authentication hub.docker.com/settings/security 🔴 REQUIRED

---

12. AI Self-Coder — Complete Examples & Behaviors

Production-Grade Workflow Orchestration

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    PRODUCTION WORKFLOW ORCHESTRATION                            │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  TRIGGER: Push to main OR scheduled (every 15 min) OR manual                    │
│                                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  LAYER 1: VALIDATION (maid-ci.yml)                                      │   │
│  │  ├── Validate YAML syntax                                               │   │
│  │  ├── Validate Task.md format                                            │   │
│  │  ├── Check secrets exist                                                │   │
│  │  └── Lint Python code                                                   │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                      │                                           │
│                                      ▼ (ONLY IF VALID)                          │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  LAYER 2: SECURITY (maid-security.yml)                                  │   │
│  │  ├── Scan for exposed tokens                                            │   │
│  │  ├── Run Trivy vulnerability scan                                       │   │
│  │  └── Check dependencies                                                 │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                      │                                           │
│                                      ▼ (ONLY IF SECURE)                         │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  LAYER 3: EXECUTION (maid-executor.yml)                                 │   │
│  │  ├── Scan Task.md for 'new'                                             │   │
│  │  ├── Route to best AI model                                             │   │
│  │  ├── Execute task                                                       │   │
│  │  └── Update status                                                      │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                      │                                           │
│                                      ▼ (ONLY IF SUCCESS)                        │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  LAYER 4: DEPLOYMENT (docker-build + docker-push + hf-sync)             │   │
│  │  ├── Build Docker image                                                 │   │
│  │  ├── Push to Docker Hub                                                 │   │
│  │  ├── Update hf.Dockerfile                                               │   │
│  │  └── Sync to Hugging Face Space                                         │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                      │                                           │
│                                      ▼                                          │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  LAYER 5: RELEASE (maid-release.yml)                                    │   │
│  │  ├── Create version tag                                                 │   │
│  │  ├── Generate release notes                                             │   │
│  │  └── Attach CHANGELOG                                                   │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                                                                  │
│  BACKGROUND SERVICES (Run continuously):                                        │
│  - maid-scheduler.yml (every 15 min)                                           │
│  - maid-retry-engine.yml (handle failures)                                     │
│  - maid-monitor.yml (health checks)                                           │
│  - maid-issue-bot.yml (create issues on failure)                              │
│  - maid-rollback.yml (disaster recovery)                                      │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

13. Production-Grade Workflow Stack

13.1 maid-ci.yml — Pre-Execution Validator ⚠️ CRITICAL

```yaml
name: CI Validator

on:
  pull_request:
    branches: [ main ]
  push:
    branches: [ main ]
  workflow_dispatch:

jobs:
  validate:
    name: Validate Input
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Validate Task.md format
        run: |
          if ! grep -q "| # | Task | Description" Task.md; then
            echo "❌ Task.md has invalid format"
            exit 1
          fi
          echo "✅ Task.md format valid"
      
      - name: Validate YAML workflows
        run: |
          for file in .github/workflows/*.yml; do
            python -c "import yaml; yaml.safe_load(open('$file'))"
            echo "✅ $file valid"
          done
      
      - name: Check secrets existence
        run: |
          if [ -z "$HF_TOKEN" ]; then
            echo "⚠️ HF_TOKEN missing"
          fi
          if [ -z "$DOCKERHUB_TOKEN" ]; then
            echo "⚠️ DOCKERHUB_TOKEN missing"
          fi
      
      - name: Lint Python
        run: |
          pip install pylint
          find . -name "*.py" -exec pylint {} \; || true
      
      - name: Validate no 'new' tasks without Roadmap
        run: |
          NEW_TASKS=$(grep -c '| new ' Task.md || echo "0")
          if [ "$NEW_TASKS" -gt 0 ]; then
            echo "⚠️ $NEW_TASKS pending tasks — will trigger AI"
          fi
```

13.2 maid-security.yml — Security & Vulnerability Scan ⚠️ CRITICAL

```yaml
name: Security Scanner

on:
  push:
    branches: [ main ]
  schedule:
    - cron: "0 */6 * * *"
  workflow_dispatch:

jobs:
  security:
    name: Security Scan
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Check for exposed secrets
        run: |
          if grep -r "HF_TOKEN\|GEMINI_API_KEY\|DOCKERHUB_TOKEN" . --exclude-dir=.git; then
            echo "❌ CRITICAL: Exposed secrets found!"
            exit 1
          fi
          echo "✅ No exposed secrets"
      
      - name: Run Trivy vulnerability scan
        uses: aquasecurity/trivy-action@master
        with:
          scan-type: 'fs'
          scan-ref: '.'
          format: 'table'
      
      - name: Check Dockerfile for security issues
        run: |
          if [ -f "Dockerfile" ]; then
            docker run --rm -i hadolint/hadolint < Dockerfile
            echo "✅ Dockerfile linted"
          fi
```

13.3 maid-scheduler.yml — Autonomous Runner ⚠️ CRITICAL

```yaml
name: Autonomous Scheduler

on:
  schedule:
    - cron: "*/15 * * * *"
  workflow_dispatch:

jobs:
  schedule:
    name: Run Scheduled Tasks
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Check for pending tasks
        id: check
        run: |
          PENDING=$(grep -c '| new ' Task.md || echo "0")
          echo "pending=$PENDING" >> $GITHUB_OUTPUT
          if [ "$PENDING" -gt 0 ]; then
            echo "📅 $PENDING tasks pending — triggering execution"
          fi
      
      - name: Trigger AI execution
        if: steps.check.outputs.pending != '0'
        run: |
          gh workflow run maid-executor.yml
        env:
          GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

13.4 maid-retry-engine.yml — Failure Recovery ⚠️ CRITICAL

```yaml
name: Retry Engine

on:
  workflow_run:
    workflows: ["AI Self-Coder — MAID Executor"]
    types: [completed]
  workflow_dispatch:

jobs:
  retry:
    name: Handle Failures
    runs-on: ubuntu-latest
    if: ${{ github.event.workflow_run.conclusion == 'failure' }}
    steps:
      - uses: actions/checkout@v4
      
      - name: Analyze failure
        id: analyze
        run: |
          FAILED_TASKS=$(grep '| ❌ ' Task.md | wc -l)
          echo "failed=$FAILED_TASKS" >> $GITHUB_OUTPUT
          
          if [ "$FAILED_TASKS" -gt 0 ]; then
            echo "🔄 $FAILED_TASKS failed tasks — resetting to retry"
            sed -i 's/| ❌ |/| new |/g' Task.md
            git add Task.md
            git commit -m "retry: reset failed tasks" || true
            git push origin main
          fi
      
      - name: Re-trigger execution
        if: steps.analyze.outputs.failed != '0'
        run: |
          gh workflow run maid-executor.yml
        env:
          GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

13.5 maid-release.yml — Version & Release Manager ⚠️ CRITICAL

```yaml
name: Release Manager

on:
  push:
    tags:
      - 'v*'
  workflow_dispatch:
    inputs:
      version:
        description: 'Version to release (e.g., v1.2.3)'
        required: true

jobs:
  release:
    name: Create Release
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0
      
      - name: Get version
        id: version
        run: |
          if [ -n "${{ github.event.inputs.version }}" ]; then
            VERSION="${{ github.event.inputs.version }}"
          else
            VERSION="${GITHUB_REF_NAME}"
          fi
          echo "version=$VERSION" >> $GITHUB_OUTPUT
      
      - name: Generate release notes
        run: |
          echo "# ${{ steps.version.outputs.version }}" > RELEASE_NOTES.md
          echo "" >> RELEASE_NOTES.md
          echo "## What's Changed" >> RELEASE_NOTES.md
          grep "✅" Task.md | awk -F'|' '{print "- " $3}' >> RELEASE_NOTES.md
          echo "" >> RELEASE_NOTES.md
          echo "## Full Changelog" >> RELEASE_NOTES.md
          echo "- [CHANGELOG.md](CHANGELOG.md)" >> RELEASE_NOTES.md
      
      - name: Create GitHub Release
        uses: softprops/action-gh-release@v1
        with:
          tag_name: ${{ steps.version.outputs.version }}
          name: ${{ steps.version.outputs.version }}
          body_path: RELEASE_NOTES.md
          draft: false
          prerelease: false
```

13.6 maid-rollback.yml — Disaster Recovery ⚠️ CRITICAL

```yaml
name: Rollback System

on:
  workflow_dispatch:
    inputs:
      backup_version:
        description: 'Backup version to restore (e.g., v1.2.2)'
        required: true

jobs:
  rollback:
    name: Rollback to Backup
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Restore from backup
        run: |
          BACKUP_FILE=".github/backups/original_${{ github.event.inputs.backup_version }}.backup"
          if [ -f "$BACKUP_FILE" ]; then
            tar -xzf "$BACKUP_FILE" --overwrite
            echo "✅ Restored from $BACKUP_FILE"
          else
            echo "❌ Backup $BACKUP_FILE not found"
            exit 1
          fi
      
      - name: Reset version
        run: |
          sed -i "s/v[0-9]*\.[0-9]*\.[0-9]*/${{ github.event.inputs.backup_version }}/g" Roadmap.md
          git add .
          git commit -m "rollback: restored to ${{ github.event.inputs.backup_version }}"
          git tag "${{ github.event.inputs.backup_version }}" --force
          git push origin main --force
          git push origin "${{ github.event.inputs.backup_version }}" --force
      
      - name: Re-trigger deployment
        run: |
          gh workflow run docker-build.yml
        env:
          GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

13.7 maid-monitor.yml — Health Monitoring

```yaml
name: Health Monitor

on:
  schedule:
    - cron: "*/30 * * * *"
  workflow_dispatch:

jobs:
  monitor:
    name: Check Health
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Check workflow success rates
        run: |
          FAILED=$(gh run list --limit 100 --json conclusion \
            | jq '[.[] | select(.conclusion == "failure")] | length')
          TOTAL=$(gh run list --limit 100 --json conclusion | jq 'length')
          SUCCESS_RATE=$(( (TOTAL - FAILED) * 100 / TOTAL ))
          
          echo "📊 Success rate: $SUCCESS_RATE%"
          if [ "$SUCCESS_RATE" -lt 80 ]; then
            echo "⚠️ Success rate below 80%"
          fi
        env:
          GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      
      - name: Check pending tasks age
        run: |
          OLD_TASKS=$(grep '| new ' Task.md | head -5)
          if [ -n "$OLD_TASKS" ]; then
            echo "⚠️ Pending tasks detected:"
            echo "$OLD_TASKS"
          fi
```

13.8 maid-issue-bot.yml — Auto Issue Creator

```yaml
name: Issue Bot

on:
  workflow_run:
    workflows: ["AI Self-Coder — MAID Executor"]
    types: [completed]
  workflow_dispatch:

jobs:
  create-issues:
    name: Create Issues on Failure
    runs-on: ubuntu-latest
    if: ${{ github.event.workflow_run.conclusion == 'failure' }}
    steps:
      - uses: actions/checkout@v4
      
      - name: Create issue for failed tasks
        run: |
          FAILED_TASKS=$(grep '| ❌ ' Task.md)
          if [ -n "$FAILED_TASKS" ]; then
            gh issue create \
              --title "AI Execution Failed: Tasks need attention" \
              --body "## Failed Tasks\n\n$FAILED_TASKS\n\n## Next Steps\n1. Check Notes column for errors\n2. Fix the issue\n3. Reset status to 'new'\n4. Retry execution" \
              --label "bug,ai-failure"
          fi
        env:
          GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

13.9 docker-build.yml — Build Image Only

```yaml
name: Docker Build

on:
  push:
    branches: [ main ]
    paths:
      - 'Dockerfile'
      - '**.py'
  workflow_dispatch:

jobs:
  build:
    name: Build Docker Image
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Get version
        id: version
        run: |
          VERSION=$(grep -oP 'v\d+\.\d+\.\d+' Roadmap.md | head -1)
          echo "version=$VERSION" >> $GITHUB_OUTPUT
      
      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3
      
      - name: Build image
        uses: docker/build-push-action@v5
        with:
          context: .
          load: true
          tags: |
            hoopstreet/tiktok-prompt-generator:${{ steps.version.outputs.version }}
            hoopstreet/tiktok-prompt-generator:latest
          cache-from: type=gha
          cache-to: type=gha,mode=max
      
      - name: Save image to artifact
        run: |
          docker save hoopstreet/tiktok-prompt-generator:${{ steps.version.outputs.version }} \
            | gzip > docker-image.tar.gz
      
      - name: Upload artifact
        uses: actions/upload-artifact@v4
        with:
          name: docker-image
          path: docker-image.tar.gz
```

13.10 docker-push.yml — Push to Docker Hub

```yaml
name: Docker Push

on:
  workflow_run:
    workflows: ["Docker Build"]
    types: [completed]
  workflow_dispatch:

jobs:
  push:
    name: Push to Docker Hub
    runs-on: ubuntu-latest
    if: ${{ github.event.workflow_run.conclusion == 'success' }}
    steps:
      - uses: actions/checkout@v4
      
      - name: Download artifact
        uses: actions/download-artifact@v4
        with:
          name: docker-image
          github-token: ${{ secrets.GITHUB_TOKEN }}
          run-id: ${{ github.event.workflow_run.id }}
      
      - name: Load image
        run: |
          gunzip -c docker-image.tar.gz | docker load
      
      - name: Login to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      
      - name: Get version
        id: version
        run: |
          VERSION=$(grep -oP 'v\d+\.\d+\.\d+' Roadmap.md | head -1)
          echo "version=$VERSION" >> $GITHUB_OUTPUT
      
      - name: Push to Docker Hub
        run: |
          docker push hoopstreet/tiktok-prompt-generator:${{ steps.version.outputs.version }}
          docker push hoopstreet/tiktok-prompt-generator:latest
```

13.11 hf-sync.yml — Sync to Hugging Face

```yaml
name: Hugging Face Sync

on:
  workflow_run:
    workflows: ["Docker Push"]
    types: [completed]
  workflow_dispatch:

jobs:
  sync:
    name: Sync to HF Space
    runs-on: ubuntu-latest
    if: ${{ github.event.workflow_run.conclusion == 'success' }}
    steps:
      - uses: actions/checkout@v4
      
      - name: Get version
        id: version
        run: |
          VERSION=$(grep -oP 'v\d+\.\d+\.\d+' Roadmap.md | head -1)
          echo "version=$VERSION" >> $GITHUB_OUTPUT
      
      - name: Update hf.Dockerfile
        run: |
          sed -i "s|FROM .*|FROM hoopstreet/tiktok-prompt-generator:${{ steps.version.outputs.version }}|g" hf.Dockerfile
          git add hf.Dockerfile
          git commit -m "ai: update hf.Dockerfile to ${{ steps.version.outputs.version }}" || true
          git push origin main
      
      - name: Sync to Hugging Face Space
        env:
          HF_TOKEN: ${{ secrets.HF_TOKEN }}
        run: |
          git clone https://hoopstreet:$HF_TOKEN@huggingface.co/spaces/hoopstreet/TikTok-Prompt-Generator hf_space
          cp Dockerfile hf_space/
          cp README.md hf_space/
          cd hf_space
          git config user.name "AI Self-Coder"
          git config user.email "ai@maid-protocol.local"
          git add Dockerfile README.md
          git commit -m "Sync from GitHub: ${{ steps.version.outputs.version }}" || true
          git push origin main
          
          echo "✅ Synced to Hugging Face Space"
```

---

14. Complete Workflow Cycle

Production-Grade Orchestration Flow

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    PRODUCTION-GRADE ORCHESTRATION FLOW                          │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  TRIGGER: Push to main OR Scheduled (every 15 min) OR Manual            │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                      │                                           │
│                                      ▼                                           │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  LAYER 1: VALIDATION (maid-ci.yml)                                      │   │
│  │  ├── Validate YAML ──────────────────────────────────────────────┐     │   │
│  │  ├── Validate Task.md                                              │     │   │
│  │  ├── Check secrets                                                 │     │   │
│  │  └── Lint Python                                                   │     │   │
│  └─────────────────────────────────────────────────────────────────────┼───┘   │
│                                      │                                   │       │
│                                      ▼                                   │       │
│                              ┌───────┴───────┐                          │       │
│                              │  VALID?       │                          │       │
│                              └───────┬───────┘                          │       │
│                                      │                                   │       │
│                          ┌───────────┴───────────┐                       │       │
│                          │ YES                   │ NO                    │       │
│                          ▼                       ▼                       │       │
│  ┌─────────────────────────────────┐  ┌─────────────────────────────┐   │       │
│  │  LAYER 2: SECURITY              │  │  ❌ Block Push              │   │       │
│  │  (maid-security.yml)            │  │  Create Issue               │   │       │
│  │  ├── Secret scan                │  │  Notify Human               │   │       │
│  │  ├── Trivy scan                 │  └─────────────────────────────┘   │       │
│  │  └── Dependency check           │                                   │       │
│  └─────────────────────────────────┘                                   │       │
│                                      │                                   │       │
│                                      ▼                                   │       │
│                              ┌───────┴───────┐                          │       │
│                              │  SECURE?      │                          │       │
│                              └───────┬───────┘                          │       │
│                                      │                                   │       │
│                          ┌───────────┴───────────┐                       │       │
│                          │ YES                   │ NO                    │       │
│                          ▼                       ▼                       │       │
│  ┌─────────────────────────────────┐  ┌─────────────────────────────┐   │       │
│  │  LAYER 3: EXECUTION             │  │  ❌ Security Violation      │   │       │
│  │  (maid-executor.yml)            │  │  Create Security Issue      │   │       │
│  │  ├── Scan for 'new'             │  │  Block Deployment           │   │       │
│  │  ├── Route to AI model          │  └─────────────────────────────┘   │       │
│  │  ├── Execute task               │                                   │       │
│  │  └── Update status              │                                   │       │
│  └─────────────────────────────────┘                                   │       │
│                                      │                                   │       │
│                                      ▼                                   │       │
│                              ┌───────┴───────┐                          │       │
│                              │  SUCCESS?     │                          │       │
│                              └───────┬───────┘                          │       │
│                                      │                                   │       │
│                          ┌───────────┴───────────┐                       │       │
│                          │ YES                   │ NO                    │       │
│                          ▼                       ▼                       │       │
│  ┌─────────────────────────────────┐  ┌─────────────────────────────┐   │       │
│  │  LAYER 4: DEPLOYMENT            │  │  LAYER 4b: RETRY            │   │       │
│  │  (docker-build + push + hf)     │  │  (maid-retry-engine.yml)    │   │       │
│  │  ├── Build image                │  │  ├── Reset failed tasks     │   │       │
│  │  ├── Push to Docker Hub         │  │  ├── Max 8 attempts         │   │       │
│  │  ├── Update hf.Dockerfile       │  │  └── "Need Human" after 8   │   │       │
│  │  └── Sync to HF Space           │  └─────────────────────────────┘   │       │
│  └─────────────────────────────────┘                                   │       │
│                                      │                                   │       │
│                                      ▼                                   │       │
│  ┌─────────────────────────────────────────────────────────────────┐   │       │
│  │  LAYER 5: RELEASE (maid-release.yml)                            │   │       │
│  │  ├── Create version tag                                         │   │       │
│  │  ├── Generate release notes                                     │   │       │
│  │  └── Attach CHANGELOG                                           │   │       │
│  └─────────────────────────────────────────────────────────────────┘   │       │
│                                                                          │       │
│  BACKGROUND SERVICES:                                                     │       │
│  ┌─────────────────────────────────────────────────────────────────┐   │       │
│  │  • maid-scheduler.yml (every 15 min) — Autonomous execution    │   │       │
│  │  • maid-monitor.yml (health checks) — Observability            │   │       │
│  │  • maid-issue-bot.yml (auto-issues) — Error tracking           │   │       │
│  │  • maid-rollback.yml (disaster recovery) — Safety net          │   │       │
│  └─────────────────────────────────────────────────────────────────┘   │       │
│                                                                          │       │
│  FINAL RESULT:                                                            │       │
│  ✅ GitHub Tag: v1.2.3                                                    │       │
│  ✅ Docker Hub: hoopstreet/tiktok-prompt-generator:v1.2.3                │       │
│  ✅ hf.Dockerfile: Updated with matching tag                             │       │
│  ✅ Hugging Face Space: Synced and running                               │       │
│  ✅ Release created with notes                                           │       │
│  ✅ All versions match                                                   │       │
│                                                                          │       │
└──────────────────────────────────────────────────────────────────────────┘       │
                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

15. Error Recovery Protocol

Automatic Error Handling (8 Attempts Max + System-Wide Retry)

Attempt Action System
1 Execute with Priority 1 model maid-executor.yml
2 Execute with Priority 2 model maid-executor.yml
3 Execute with Priority 3 model maid-executor.yml
4 Execute with Priority 4 model maid-executor.yml
5 Execute with Priority 5 (Gemini) maid-executor.yml
6 Execute with simplified approach maid-executor.yml
7 Execute with debug mode enabled maid-executor.yml
8 Final attempt with all fallbacks maid-executor.yml
After 8 System-wide retry maid-retry-engine.yml
After retry fails Create GitHub Issue maid-issue-bot.yml
Critical failure Rollback to backup maid-rollback.yml

"Need Human" Status + Auto-Issue

```bash
# When AI Self-Coder cannot fix after 8 attempts:
1. Status changed to "Need Human"
2. Error description added to Notes column
3. maid-issue-bot.yml creates GitHub Issue
4. Issue labeled "ai-failure", "bug"
5. AI moves to next task
6. Human gets notified via GitHub Issue
```

Manual Recovery (Human Coder)

```bash
cd ~/TikTok-Prompt-Generator || exit

# View failed tasks
grep "Need Human" Task.md

# View open issues
gh issue list --label "ai-failure"

# Reset failed task to 'new' after fixing
sed -i 's/| Need Human |/| new |/g' Task.md

# Push to retry
git add Task.md
git commit -m "fix: reset failed task for retry"
git pull origin main --rebase
git push origin main

# Close issue
gh issue close <ISSUE_NUMBER> --comment "Fixed by human"

# BLANK LINE
```

Disaster Recovery (Rollback)

```bash
# Trigger rollback workflow
gh workflow run maid-rollback.yml -f backup_version=v1.2.2

# Or manually:
cd ~/TikTok-Prompt-Generator || exit
git checkout v1.2.2
git checkout -b hotfix/rollback
git push origin hotfix/rollback
# Create PR, merge, deploy
```

---

16. Status Legend

Symbol Meaning Who Sets It Next Action
new Ready for AI Human Coder Push to trigger
⌛ AI executing AI Self-Coder Wait 2-5 min
✅ Complete AI Self-Coder Unblocks next task
❌ Error AI Self-Coder Retry engine will reset
⚠️ Warning AI Self-Coder Manual intervention
📅 Scheduled Human Coder Waiting for milestone
Need Human 8 attempts failed AI Self-Coder Human must fix + issue created

---

17. Current Status Dashboard

Task.md Status (Production)

# Task Status Dev
1 iSH Environment Setup ✅ Human Coder
2 GitHub Auth Setup ✅ Human Coder
3 GitHub Secrets Config ✅ Human Coder
4 AI Self-Coder Developer new Human Coder
5 AI Self-Coder Multi-Model new Human Coder
6 CI Validator (maid-ci.yml) new Human Coder
7 Security Scanner (maid-security.yml) new Human Coder
8 Scheduler (maid-scheduler.yml) new Human Coder
9 Retry Engine (maid-retry-engine.yml) new Human Coder
10 Release Manager (maid-release.yml) new Human Coder
11 Rollback System (maid-rollback.yml) new Human Coder
12 Monitor & Issue Bot 📅 AI Self-Coder
13 Docker Pipeline 📅 AI Self-Coder
14 Testing & Lint 📅 AI Self-Coder
15 Business Logic 📅 AI Self-Coder

Workflow Implementation Status

Workflow Status Criticality
maid-ci.yml new 🔴 CRITICAL
maid-security.yml new 🔴 CRITICAL
maid-scheduler.yml new 🔴 CRITICAL
maid-retry-engine.yml new 🔴 CRITICAL
maid-release.yml new 🔴 CRITICAL
maid-rollback.yml new 🔴 CRITICAL
maid-executor.yml new ✅ REQUIRED
maid-monitor.yml 📅 🟡 HIGH
maid-issue-bot.yml 📅 🟡 HIGH
docker-build.yml 📅 ✅ REQUIRED
docker-push.yml 📅 ✅ REQUIRED
hf-sync.yml 📅 ✅ REQUIRED

Required Secrets Status

Secret Status Action Needed
HF_TOKEN ❌ Missing Add to GitHub Secrets
GEMINI_API_KEY ❌ Missing Add to GitHub Secrets
DOCKERHUB_USERNAME ❌ Missing Add to GitHub Secrets
DOCKERHUB_TOKEN ❌ Missing Add to GitHub Secrets

---

📋 Summary

The Golden Rules (Production-Grade)

1. Human Coder builds ALL 17 production-grade workflows. AI Self-Coder auto-scales to complete everything else.

2. Validation → Security → Execution → Deployment → Release (5-layer pipeline)

3. 8 attempts max → system-wide retry engine → auto-issue → rollback if needed

4. Model Priority: DeepSeek → Qwen → Llama → StarCoder → Gemini (Backup)

5. Version Sync Authority: GitHub → Docker Hub → Hugging Face (ALL MATCH)

Priority Implementation Order (MUST BUILD FIRST)

Priority Workflow Purpose
🔴 1 maid-ci.yml Pre-execution validator
🔴 2 maid-security.yml Security & vulnerability scan
🔴 3 maid-scheduler.yml Autonomous runner (every 15 min)
🔴 4 maid-retry-engine.yml Failure recovery system
🔴 5 maid-release.yml Version & release manager
🔴 6 maid-rollback.yml Disaster recovery
🟡 7 maid-monitor.yml Health monitoring
🟡 8 maid-issue-bot.yml Auto issue creator
🟢 9 docker-build + push + hf-sync Deployment pipeline
🟢 10 maid-test + maid-lint Quality assurance

Files Summary (Production)

File Content Owner Criticality
Task.md 15 tasks (Kanban style) Human Coder ✅ REQUIRED
Roadmap.md 5 sections (Story style) Human Coder ✅ REQUIRED
maid-ci.yml Pre-execution validator Human Coder 🔴 CRITICAL
maid-security.yml Security scanner Human Coder 🔴 CRITICAL
maid-scheduler.yml Autonomous runner Human Coder 🔴 CRITICAL
maid-retry-engine.yml Failure recovery Human Coder 🔴 CRITICAL
maid-release.yml Release manager Human Coder 🔴 CRITICAL
maid-rollback.yml Disaster recovery Human Coder 🔴 CRITICAL
maid-executor.yml AI brain Human Coder ✅ REQUIRED
CHANGELOG.md Auto-generated AI Self-Coder 🟡 HIGH
.github/backups/ Original backups AI Self-Coder 🟡 HIGH

---

MAID Protocol — Production-Grade Complete Roadmap.md
TikTok-Prompt-Generator · Version 0.4.0

Lead Developer: hoopstreet
Email: hoopstreet143@gmail.com
GitHub: hoopstreet
Repository: https://github.com/hoopstreet/TikTok-Prompt-Generator

Status: ✅ Human Coder Foundation Complete | ⌛ 11 Critical Workflows Ready to Deploy | ⏳ Add Secrets to GitHub

Architecture: Production-Grade DevOps AI Platform
Workflows: 17 Modular (Validation → Security → Execution → Deployment → Release)
Availability: 24/7 (Scheduled every 15 min + Push-triggered)
Recovery: 8 attempts + Retry Engine + Rollback System + Auto-Issues

```
```
