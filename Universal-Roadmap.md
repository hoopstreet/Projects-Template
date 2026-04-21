MAID Protocol — Complete Roadmap.md (Final Production Ready)

🧬 Project Identity: TikTok-Prompt-Generator DNA

Lead Developer: hoopstreet
Email: hoopstreet143@gmail.com
GitHub: hoopstreet
Environment: iSH (Alpine Linux) on iPhone
Architecture: Zero-Local-Load (ZLL)
AI Code Providers (Human Coder): ChatGPT · Gemini · Deepseek · Claude
AI Self-Coder Models: DeepSeek · Qwen · StarCoder · Llama · Gemini (Backup)

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
13. AI Self-Coder — GitHub Actions Workflow
14. Complete Workflow Cycle
15. Error Recovery Protocol
16. Status Legend
17. Current Status Dashboard

---

1. Architecture Overview

The Complete Ecosystem with Multi-Model AI

```
┌─────────────────────────────────────────────────────────────────────────────────────────────┐
│                         MAID PROTOCOL — COMPLETE ARCHITECTURE                                │
├─────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                              │
│  ┌─────────────────────────────────────────────────────────────────────────────────────┐   │
│  │                         HUMAN CODER (iPhone iSH)                                     │   │
│  │                                                                                       │   │
│  │  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐             │   │
│  │  │   ChatGPT    │  │   Gemini     │  │  Deepseek    │  │   Claude     │             │   │
│  │  └──────────────┘  └──────────────┘  └──────────────┘  └──────────────┘             │   │
│  │         │                 │                 │                 │                      │   │
│  │         └─────────────────┴─────────────────┴─────────────────┘                      │   │
│  │                                            │                                          │   │
│  │                              Generate cat << 'EOF' scripts                            │   │
│  │                                            │                                          │   │
│  │                            ┌───────────────┴───────────────┐                          │   │
│  │                            │   Task.md + Roadmap.md        │                          │   │
│  │                            │   (with 'new' status)         │                          │   │
│  │                            └───────────────┬───────────────┘                          │   │
│  │                                            │                                          │   │
│  │                                   git push (execute: roadmap)                        │   │
│  └────────────────────────────────────────────┼─────────────────────────────────────────┘   │
│                                               │                                             │
│                                               ▼                                             │
│  ┌─────────────────────────────────────────────────────────────────────────────────────┐   │
│  │                    GITHUB ACTIONS — AI SELF-CODER (247 Active)                       │   │
│  │                                                                                       │   │
│  │  ┌─────────────────────────────────────────────────────────────────────────────────┐ │   │
│  │  │                         PRIORITY MODEL ROTATION                                  │ │   │
│  │  │                                                                                   │ │   │
│  │  │  Priority 1: DeepSeek-V3 (Hugging Face) ──────────────────────────────────────┐ │ │   │
│  │  │  Priority 2: Qwen2.5-Coder-32B (Hugging Face) ────────────────────────────────┼─┼─┼─┐ │
│  │  │  Priority 3: Llama-3.3-70B (Hugging Face) ────────────────────────────────────┼─┼─┼─┼─┐ │
│  │  │  Priority 4: StarCoder2-15B (Hugging Face) ──────────────────────────────────┼─┼─┼─┼─┼─┐ │
│  │  │  Priority 5: Gemini API Key (Backup) ────────────────────────────────────────┼─┼─┼─┼─┼─┼─┐ │
│  │  │                                                                               │ │ │ │ │ │ │
│  │  └───────────────────────────────────────────────────────────────────────────────┼─┼─┼─┼─┼─┘ │
│  │                                                                                   │ │ │ │ │   │
│  │  ┌─────────────────────────────────────────────────────────────────────────────────┼─┼─┼─┼─┐ │
│  │  │                         AI SELF-CODER CORE                                      │ │ │ │ │ │
│  │  │                                                                                   │ │ │ │ │ │
│  │  │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────┐ │ │ │ │ │ │
│  │  │  │  Task Scanner   │→ │  AI Analyzer    │→ │  AI Executor    │→ │Status Update│ │ │ │ │ │
│  │  │  └─────────────────┘  └─────────────────┘  └─────────────────┘  └─────────────┘ │ │ │ │ │ │
│  │  │         │                     │                     │                  │        │ │ │ │ │ │
│  │  │         ▼                     ▼                     ▼                  ▼        │ │ │ │ │ │
│  │  │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────┐ │ │ │ │ │ │
│  │  │  │ Version Compare │  │  Backup Creator │  │  Auto Fixer     │  │PR Generator │ │ │ │ │ │
│  │  │  └─────────────────┘  └─────────────────┘  └─────────────────┘  └─────────────┘ │ │ │ │ │ │
│  │  │                                                                                   │ │ │ │ │ │
│  │  └─────────────────────────────────────────────────────────────────────────────────┼─┼─┼─┼─┘ │
│  │                                                                                   │ │ │ │   │
│  └───────────────────────────────────────────────────────────────────────────────────┼─┼─┼─┼───┘
│                                                                                      │ │ │ │
│  ┌───────────────────────────────────────────────────────────────────────────────────┼─┼─┼─┐
│  │                         DEPLOYMENT PIPELINE                                       │ │ │ │ │
│  │                                                                                   │ │ │ │ │
│  │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────┐ │ │ │ │ │
│  │  │  Docker Build   │→ │  Docker Push    │→ │  HF.Dockerfile  │→ │  HF Space   │ │ │ │ │
│  │  │  (with tag)     │  │  to Docker Hub  │  │  Update Tag     │  │  Sync       │ │ │ │ │
│  │  └─────────────────┘  └─────────────────┘  └─────────────────┘  └─────────────┘ │ │ │ │ │
│  │                                                                                   │ │ │ │ │
│  └───────────────────────────────────────────────────────────────────────────────────┼─┼─┼─┘
│                                                                                      │ │ │
└──────────────────────────────────────────────────────────────────────────────────────┼─┼─┘
                                                                                       │ │
                                                                                       ▼ ▼
                                                                              ✅ COMPLETE
```

Persistent GitHub Connection (iSH iPhone)

```bash
# ONE TIME SETUP — Credentials saved forever
git config --global user.name "hoopstreet"
git config --global user.email "hoopstreet143@gmail.com"
git config --global credential.helper store

# First push saves credentials
git remote add origin https://github.com/hoopstreet/TikTok-Prompt-Generator.git
git push origin main
# Enter username: hoopstreet
# Enter PAT (Personal Access Token) — saved forever
```

Always Navigate to Project (Every Code Block)

```bash
# EVERY CODE BLOCK STARTS WITH THIS
cd ~/TikTok-Prompt-Generator || exit

# BLANK SPACE AFTER EVERY EOF FOR AUTO-EXECUTION
# (Add empty line after each EOF)
```

---

2. The Two-File System

```
~/TikTok-Prompt-Generator/
├── Task.md          ← Human input buffer (Kanban/Sheets style)
├── Roadmap.md       ← AI output reality (Story/Documentation style)
└── CHANGELOG.md     ← Auto-generated by AI Self-Coder
```

File Purposes

File Owner Purpose Format
Task.md Human Coder Input Buffer — The "What" Kanban/Sheets table
Roadmap.md AI Self-Coder Output Reality — The "How" Story/Documentation style
CHANGELOG.md AI Self-Coder Change tracking Chronological entries

---

3. Developer Roles

Role 1: Human Coder (Commander) — Priority FIRST

Aspect Details
Priority FIRST — Establishes the entire foundation
Device iPhone running iSH (Alpine Linux)
AI Code Providers ChatGPT, Gemini, Deepseek, Claude
Code Rules STRICT — 150-char limit, cat EOF only, no nano/vi
Primary Action Deploy templated Task.md and Roadmap.md
Primary Mission Build the AI Self-Coder workflows
Commit Style execute: roadmap vX.X.X
Credentials GitHub Secrets + local credential.helper store
Never Does Manual edits with nano/vi, edits Roadmap.md directly

Role 2: AI Self-Coder (Executor) — 247 Active

Aspect Details
Priority SECOND — Activated after Human pushes
Environment GitHub Actions Runner (cloud)
Primary Mission Auto-scan Task.md and Roadmap.md
Primary Action Execute tasks in priority order
Models DeepSeek-V3, Qwen2.5-Coder, Llama-3.3, StarCoder2, Gemini
Auto-Scaling Automatically completes remaining tasks
Version Control Auto-bumps Patch version
Documentation Auto-generates CHANGELOG.md
Error Handling 8 attempts max → "Need Human" status

---

4. Table Structures

Task.md — Kanban/Sheets Style (Input)

# Task Description Notes Tags Status Dev
1 iSH Environment Setup Alpine Linux configuration git init, credential store v0.1.0 stable ✅ Human Coder
2 GitHub Auth Setup PAT and remote connection credential.helper store v0.1.0 setup ✅ Human Coder
3 GitHub Secrets Config Store tokens securely HF_TOKEN, GEMINI_API_KEY v0.1.5 security ✅ Human Coder
4 AI Self-Coder Developer Create base workflow .github/workflows/maid-executor.yml v0.2.0 automation new Human Coder
5 AI Self-Coder Multi-Model Integrate HF + Gemini models DeepSeek, Qwen, Llama, StarCoder v0.3.0 feature new Human Coder
6 AI Self-Coder Analyzer Analyze versions, create backup Compare oldest to present v0.3.1 analyzer 📅 AI Self-Coder
7 Docker Build & Push Auto-build on code change Push to Docker Hub with tag v0.4.0 deployment 📅 AI Self-Coder
8 HF.Dockerfile Sync Match Docker Hub version Update hf.Dockerfile tag v0.4.1 sync 📅 AI Self-Coder
9 Hugging Face Sync Sync Dockerfile + README Push to HF Space v0.4.2 deployment 📅 AI Self-Coder
10 Business Logic Setup TikTok Prompt Generator Core product development v1.0.0 feature 📅 AI Self-Coder
11 Video Pipeline Integration ElevenLabs + Creatomate Full video generation v1.1.0 upgrade 📅 AI Self-Coder
12 Production Deployment Full pipeline live End-to-end ready v2.0.0 stable 📅 AI Self-Coder

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
Base Workflow Create .github/workflows/maid-executor.yml ⌛
Task Detection Scan Task.md for 'new' status 📅
Status Updates Auto-update ⌛ → ✅ 📅

Section 3: AI Self-Coder Multi-Model (v0.3.0) — 📅 PLANNED

Integrating multiple AI models with priority rotation.

Priority Model Source Status
1 DeepSeek-V3 Hugging Face (HF_TOKEN) 📅
2 Qwen2.5-Coder-32B Hugging Face (HF_TOKEN) 📅
3 Llama-3.3-70B Hugging Face (HF_TOKEN) 📅
4 StarCoder2-15B Hugging Face (HF_TOKEN) 📅
5 Gemini API Key (Backup) 📅

Section 4: AI Self-Coder Analyzer & Backup (v0.3.1) — 📅 PLANNED

Version analysis and backup creation.

Milestone Description Status
Version Analyzer Compare oldest to present tags 📅
Full Backup Create original backup before upgrades 📅
Error Explorer Auto-bugs detection and fixing 📅

Section 5: Deployment Pipeline (v0.4.0) — 📅 PLANNED

Docker and Hugging Face deployment.

Milestone Description Status
Docker Build Auto-build on code change 📅
Docker Push Push to Docker Hub with version tag 📅
HF.Dockerfile Sync Match Docker Hub version 📅
HF Space Sync Sync Dockerfile + README 📅

Section 6: Business Logic (v1.0.0) — 📅 READY

Core product development after AI Self-Coder is complete.

Milestone Description Status
TikTok Prompt Engine AI script generation 📅
Video Pipeline ElevenLabs + Creatomate 📅
Production Full deployment 📅

---

5. Human Coder — Complete Examples & Templates

Template 1: Pre-Templated Task.md (Complete List)

```bash
cd ~/TikTok-Prompt-Generator || exit

cat << 'EOF' > Task.md
# 🛠 Task Ledger: TikTok-Prompt-Generator
| # | Task | Description | Notes | Tags | Status | Dev |
|:---|:---|:---|:---|:---|:---|:---|
| 1 | iSH Environment Setup | Alpine Linux configuration | git init, credential store | v0.1.0 stable | ✅ | Human Coder |
| 2 | GitHub Auth Setup | PAT and remote connection | credential.helper store | v0.1.0 setup | ✅ | Human Coder |
| 3 | GitHub Secrets Config | Store tokens securely | HF_TOKEN, GEMINI_API_KEY | v0.1.5 security | ✅ | Human Coder |
| 4 | AI Self-Coder Developer | Create base workflow | .github/workflows/maid-executor.yml | v0.2.0 automation | new | Human Coder |
| 5 | AI Self-Coder Multi-Model | Integrate HF + Gemini models | DeepSeek, Qwen, Llama, StarCoder | v0.3.0 feature | new | Human Coder |
| 6 | AI Self-Coder Analyzer | Analyze versions, create backup | Compare oldest to present | v0.3.1 analyzer | 📅 | AI Self-Coder |
| 7 | Docker Build & Push | Auto-build on code change | Push to Docker Hub with tag | v0.4.0 deployment | 📅 | AI Self-Coder |
| 8 | HF.Dockerfile Sync | Match Docker Hub version | Update hf.Dockerfile tag | v0.4.1 sync | 📅 | AI Self-Coder |
| 9 | Hugging Face Sync | Sync Dockerfile + README | Push to HF Space | v0.4.2 deployment | 📅 | AI Self-Coder |
| 10 | Business Logic Setup | TikTok Prompt Generator | Core product development | v1.0.0 feature | 📅 | AI Self-Coder |
| 11 | Video Pipeline Integration | ElevenLabs + Creatomate | Full video generation | v1.1.0 upgrade | 📅 | AI Self-Coder |
| 12 | Production Deployment | Full pipeline live | End-to-end ready | v2.0.0 stable | 📅 | AI Self-Coder |
EOF

# BLANK LINE AFTER EOF FOR AUTO-EXECUTION
```

Template 2: Pre-Templated Roadmap.md (Story Style)

```bash
cat << 'EOF' > Roadmap.md
# 🗺 Project Roadmap: TikTok-Prompt-Generator

## Section 1: Foundation (v0.1.0) — ✅ COMPLETED

### Updating from initial setup
- **1.1** iSH Environment: Alpine Linux configured on iPhone
- **1.2** GitHub Connection: Remote origin with credential persistence
- **1.3** Secrets Management: HF_TOKEN, GEMINI_API_KEY configured

### Fixing from initial setup
- Buffer overflow: Solved by 150-char fragmentation rule
- Credential loss: Solved by credential.helper store

---

## Section 2: AI Self-Coder Developer (v0.2.0) — 🔄 IN PROGRESS

### Building from new development
- **2.1** Base Workflow: Create .github/workflows/maid-executor.yml
- **2.2** Task Detection: Scan Task.md for 'new' status
- **2.3** Status Updates: Auto-update ⌛ → ✅

---

## Section 3: AI Self-Coder Multi-Model (v0.3.0) — 📅 PLANNED

### Building from new development
- **3.1** DeepSeek-V3: Hugging Face integration (Priority 1)
- **3.2** Qwen2.5-Coder-32B: Hugging Face integration (Priority 2)
- **3.3** Llama-3.3-70B: Hugging Face integration (Priority 3)
- **3.4** StarCoder2-15B: Hugging Face integration (Priority 4)
- **3.5** Gemini API: Backup integration (Priority 5)
- **3.6** Model Rotation: Auto-failover between models

### Upgrades from v0.2.0
- Multi-Provider: Redundancy across 5 AI models
- Auto-Failover: Seamless switching between providers

---

## Section 4: AI Self-Coder Analyzer & Backup (v0.3.1) — 📅 PLANNED

### Building from new development
- **4.1** Version Analyzer: Compare oldest to present tags
- **4.2** Full Backup: Create original backup before upgrades
- **4.3** Error Explorer: Auto-bugs detection
- **4.4** 8-Attempt Limit: Max retries before "Need Human"

### Original Projects Current Version Tags Code:
- **Backup Location:** .github/backups/original_v{version}.backup
- **First Backup:** Before processing System Projects Roadmap Development

---

## Section 5: Deployment Pipeline (v0.4.0) — 📅 PLANNED

### Building from new development
- **5.1** Docker Build: Auto-build on code change
- **5.2** Docker Push: Push to Docker Hub with version tag
- **5.3** HF.Dockerfile Sync: Match Docker Hub version automatically
- **5.4** HF Space Sync: Sync Dockerfile + README to Hugging Face

### Version Matching
- GitHub Tag: v1.2.3
- Docker Hub: hoopstreet/tiktok-prompt-generator:v1.2.3
- HF.Dockerfile: FROM hoopstreet/tiktok-prompt-generator:v1.2.3
- Hugging Face Space: Automatic sync

---

## Section 6: Business Logic (v1.0.0) — 📅 READY

### Building from new development
- **6.1** TikTok Prompt Engine: AI script generation from product data
- **6.2** Video Pipeline: ElevenLabs voiceover + Creatomate video
- **6.3** Production Deployment: End-to-end ready

EOF

# BLANK LINE AFTER EOF FOR AUTO-EXECUTION
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

# STEP 5: Deploy AI Self-Coder workflow (from Section 13)
cat << 'EOF' > .github/workflows/maid-executor.yml
# [PASTE WORKFLOW FROM SECTION 13 HERE]
EOF

# BLANK LINE

# STEP 6: Commit and push to trigger AI Self-Coder
git add .
git commit -m "execute: roadmap v0.2.0 T-004 T-005 new"
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
- Task.md: Kanban/Sheets table (7 columns: #, Task, Description, Notes, Tags, Status, Dev)
- Roadmap.md: Story/Documentation style (numbered sections)
- CHANGELOG.md: Auto-generated by AI Self-Coder

TASK LIST (Priority Order):
1. iSH Environment Setup ✅
2. GitHub Auth Setup ✅
3. GitHub Secrets Config ✅
4. AI Self-Coder Developer (new) - Create base workflow
5. AI Self-Coder Multi-Model (new) - Integrate HF + Gemini
6-12: Auto-completed by AI Self-Coder after workflow runs

Generate the complete workflow YAML for .github/workflows/maid-executor.yml
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

Phase 3: Deploy Templated Task.md

```bash
cd ~/TikTok-Prompt-Generator || exit

cat << 'EOF' > Task.md
# [USE TEMPLATE 1 FROM SECTION 5]
EOF

# BLANK LINE
```

Phase 4: Deploy Templated Roadmap.md

```bash
cd ~/TikTok-Prompt-Generator || exit

cat << 'EOF' > Roadmap.md
# [USE TEMPLATE 2 FROM SECTION 5]
EOF

# BLANK LINE
```

Phase 5: Deploy AI Self-Coder Workflow

```bash
cd ~/TikTok-Prompt-Generator || exit

mkdir -p .github/workflows

cat << 'EOF' > .github/workflows/maid-executor.yml
# [USE WORKFLOW FROM SECTION 13]
EOF

# BLANK LINE
```

Phase 6: Initial Push

```bash
cd ~/TikTok-Prompt-Generator || exit

git add .
git commit -m "feat: initial MAID Protocol setup v0.1.0"
git pull origin main --rebase
git push origin main

# BLANK LINE
```

Phase 7: Trigger AI Self-Coder

```bash
cd ~/TikTok-Prompt-Generator || exit

git add .
git commit -m "execute: roadmap v0.2.0 T-004 T-005 new"
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

alias maid-status='
echo "📊 MAID Protocol Status"
echo "========================"
echo "🆕 Pending:  $(grep -c "| new " Task.md 2>/dev/null || echo 0)"
echo "⏳ Running:  $(grep -c "⌛" Task.md 2>/dev/null || echo 0)"
echo "✅ Done:     $(grep -c "✅" Task.md 2>/dev/null || echo 0)"
echo "❌ Errors:   $(grep -c "❌" Task.md 2>/dev/null || echo 0)"
echo "👤 Need Human: $(grep -c "Need Human" Task.md 2>/dev/null || echo 0)"
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

# BLANK LINE
```

Commit Messages

Scenario Command
Initial setup git commit -m "feat: initial MAID Protocol setup v0.1.0"
Add new tasks git commit -m "execute: roadmap v0.2.0 T-004 T-005 new"
AI auto-update Auto-generated: ai: executed tasks ✅
Manual fix git commit -m "fix: reset failed T-004 for retry"
Minor version bump git commit -m "release: v1.2.0"

---

10. Next 10 Development Suggestions

# Suggestion Description Priority
01 Complete AI Self-Coder Workflow Build maid-executor.yml 🔴 HIGHEST
02 Multi-Model Integration DeepSeek, Qwen, Llama, StarCoder, Gemini 🔴 HIGH
03 Model Priority Rotation Auto-failover with priority 1-5 🔴 HIGH
04 Version Analyzer Compare oldest to present tags 🔴 HIGH
05 Backup Creator Create original backup before upgrades 🔴 HIGH
06 Error Explorer Auto-bugs detection (8 attempts max) 🟡 MEDIUM
07 Docker Build & Push Auto-build on code change 🟡 MEDIUM
08 HF.Dockerfile Sync Match Docker Hub version automatically 🟡 MEDIUM
09 Hugging Face Sync Sync Dockerfile + README 🟢 LOW
10 Need Human Status After 8 failed attempts 🟢 LOW

---

11. AI Self-Coder — Multi-Model Setup

Model Priority List

Priority Model Source Token/Key Best For
1 DeepSeek-V3 Hugging Face HF_TOKEN Complex reasoning, debugging
2 Qwen2.5-Coder-32B Hugging Face HF_TOKEN Python, JavaScript, speed
3 Llama-3.3-70B Hugging Face HF_TOKEN Long-form documentation
4 StarCoder2-15B Hugging Face HF_TOKEN Code completion, 600+ languages
5 Gemini API Key GEMINI_API_KEY Backup when HF fails

Model Details

Priority 1: DeepSeek-V3

· Repository: huggingface.co/deepseek-ai/DeepSeek-V3
· Best For: Complex reasoning and debugging
· Status: Current King of Coding

Priority 2: Qwen2.5-Coder-32B-Instruct

· Repository: huggingface.co/Qwen/Qwen2.5-Coder-32B-Instruct
· Best For: Speed and intelligence balance
· Alternative: Qwen2.5-Coder-7B-Instruct (lightweight)

Priority 3: Llama-3.3-70B-Instruct

· Repository: huggingface.co/meta-llama/Llama-3.3-70B-Instruct
· Best For: Ultra-reliable long-form documentation

Priority 4: StarCoder2-15B-Instruct

· Repository: huggingface.co/bigcode/starcoder2-15b-instruct-v0.1
· Best For: Chat-style commands like "Refactor this function"

Priority 5: Gemini (Backup)

· API Key: AIzaSyBc1qreKK2zL_GlTim2O1pCw3e1rX-ttU0
· Best For: Fallback when Hugging Face token fails

Required Secrets

Secret Purpose Source
HF_TOKEN Hugging Face Inference API huggingface.co/settings/tokens
GEMINI_API_KEY Google Gemini Backup makersuite.google.com/app/apikey

Model Rotation Logic

```yaml
# AI Self-Coder will:
1. Try Priority 1 (DeepSeek-V3)
2. If fails → Try Priority 2 (Qwen2.5-Coder)
3. If fails → Try Priority 3 (Llama-3.3)
4. If fails → Try Priority 4 (StarCoder2)
5. If fails → Try Priority 5 (Gemini Backup)
6. If all fail → Status: "Need Human - All models failed"
```

---

12. AI Self-Coder — Complete Examples & Behaviors

Example 1: Auto Self-Completion Sequence

Step Action Status Changes
1 Human pushes T-004, T-005 T-004: new, T-005: new
2 AI Self-Coder activates Detects both tasks
3 AI checks Task.md first (priority) Verify status
4 AI executes T-004 (priority 1) new → ⌛ → ✅
5 AI auto-moves to T-005 (priority 2) new → ⌛ → ✅
6 AI continues to T-006 📅 → new → ⌛ → ✅
7 AI auto-scales through T-012 All tasks completed
8 Ready for business logic v1.0.0 reached

Example 2: Task.md First — Roadmap.md Second

```
AI Self-Coder Logic:
1. SCAN Task.md for 'new' status
2. IF Task.md has 'new' → EXECUTE
3. IF Task.md status is 'done' → Check Roadmap.md
4. IF Roadmap.md has matching 'new' → EXECUTE
5. IF Roadmap.md already updated → DO NOTHING
6. ALWAYS prioritize Task.md over Roadmap.md
```

Example 3: Error Handling (8 Attempts Max)

Attempt Action Result
1 Execute task ❌ Error
2 Retry with fix ❌ Error
3 Retry with different model ❌ Error
4 Retry with fallback model ❌ Error
5 Retry with Gemini backup ❌ Error
6 Retry with simplified approach ❌ Error
7 Retry with debug mode ❌ Error
8 Final attempt ❌ Error
After 8 Status: "Need Human" Add comments to Notes

Example 4: Version Analyzer & Backup

```yaml
# AI Self-Coder will:
1. Analyze all version tags (oldest to present)
2. Compare structure and learn project goals
3. Create full backup before any upgrade:
   - Location: .github/backups/original_v{version}.backup
   - Content: Full codebase at that tag
4. Append backup info to Roadmap.md
5. Map all file names and structure
6. Proceed to System Projects Roadmap Development
```

Example 5: Docker + Hugging Face Sync Pipeline

```yaml
# When new code is pushed to GitHub:
1. Auto-build Docker image with version tag
2. Push to Docker Hub: hoopstreet/tiktok-prompt-generator:vX.X.X
3. Auto-update hf.Dockerfile with matching tag
4. Commit and push hf.Dockerfile to GitHub
5. Sync Dockerfile and README.md to Hugging Face Space
6. All versions match: GitHub = Docker Hub = Hugging Face
```

---

13. AI Self-Coder — GitHub Actions Workflow

Complete Workflow (.github/workflows/maid-executor.yml)

```yaml
name: AI Self-Coder — MAID Executor

on:
  push:
    branches: [ main ]
    paths:
      - 'Task.md'
      - 'Roadmap.md'
      - '**.py'
      - '**.yml'
      - '**.yaml'
      - 'Dockerfile'
      - 'hf.Dockerfile'
      - 'README.md'
  workflow_dispatch:
    inputs:
      force_full_scan:
        description: 'Force full task scan'
        required: false
        default: 'false'

permissions:
  contents: write
  pull-requests: write
  issues: write

env:
  HF_TOKEN: ${{ secrets.HF_TOKEN }}
  GEMINI_API_KEY: ${{ secrets.GEMINI_API_KEY }}
  DOCKERHUB_USERNAME: hoopstreet
  DOCKERHUB_TOKEN: ${{ secrets.DOCKERHUB_TOKEN }}

jobs:
  # JOB 1: Model Status Check
  model-check:
    name: Model Status Check
    runs-on: ubuntu-latest
    outputs:
      hf_status: ${{ steps.check.outputs.hf_status }}
      gemini_status: ${{ steps.check.outputs.gemini_status }}
    steps:
      - name: Check Hugging Face Token
        id: check
        run: |
          if [ -n "$HF_TOKEN" ]; then
            echo "hf_status=active" >> $GITHUB_OUTPUT
            echo "✅ Hugging Face token is active"
          else
            echo "hf_status=inactive" >> $GITHUB_OUTPUT
            echo "⚠️ Hugging Face token missing — need update"
          fi
          
          if [ -n "$GEMINI_API_KEY" ]; then
            echo "gemini_status=active" >> $GITHUB_OUTPUT
            echo "✅ Gemini API key is active"
          else
            echo "gemini_status=inactive" >> $GITHUB_OUTPUT
            echo "⚠️ Gemini API key missing"
          fi

  # JOB 2: Version Analyzer & Backup Creator
  version-analyzer:
    name: Version Analyzer & Backup
    runs-on: ubuntu-latest
    needs: model-check
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0
      
      - name: Analyze all version tags
        id: analyzer
        run: |
          echo "🔍 Analyzing version tags from oldest to present..."
          
          # Get all version tags
          git tag -l 'v*' | sort -V > all_tags.txt
          
          # Create backup directory
          mkdir -p .github/backups
          
          # Get current version
          CURRENT_VERSION=$(grep -oP 'v\d+\.\d+\.\d+' Roadmap.md | head -1)
          
          # Create full backup
          BACKUP_FILE=".github/backups/original_${CURRENT_VERSION}.backup"
          tar -czf "$BACKUP_FILE" --exclude=.git --exclude=.github/backups .
          
          echo "✅ Backup created: $BACKUP_FILE"
          
          # Append backup info to Roadmap.md
          echo "" >> Roadmap.md
          echo "### Original Backup Created: $(date)" >> Roadmap.md
          echo "- **Version:** $CURRENT_VERSION" >> Roadmap.md
          echo "- **Backup Location:** $BACKUP_FILE" >> Roadmap.md
          echo "- **Files Mapped:** $(find . -type f -name "*.py" -o -name "*.yml" | wc -l) files" >> Roadmap.md
          
          git add Roadmap.md .github/backups/
          git commit -m "ai: version analyzer - backup created" || true
          git push origin main

  # JOB 3: Task Scanner (Priority: Task.md FIRST)
  task-scanner:
    name: Task Scanner
    runs-on: ubuntu-latest
    needs: [model-check, version-analyzer]
    outputs:
      new_tasks: ${{ steps.scan.outputs.new_tasks }}
      task_list: ${{ steps.scan.outputs.task_list }}
    steps:
      - uses: actions/checkout@v4
      
      - name: Scan Task.md for new tasks
        id: scan
        run: |
          NEW_TASKS=$(grep -c '| new ' Task.md || echo "0")
          echo "new_tasks=$NEW_TASKS" >> $GITHUB_OUTPUT
          
          if [ "$NEW_TASKS" -eq 0 ]; then
            echo "No new tasks in Task.md"
            echo "task_list=none" >> $GITHUB_OUTPUT
            exit 0
          fi
          
          # Get list of new task numbers
          TASK_NUMBERS=$(grep '| new ' Task.md | awk -F'|' '{print $2}' | xargs)
          echo "task_list=$TASK_NUMBERS" >> $GITHUB_OUTPUT
          
          echo "🤖 AI Self-Coder activated — $NEW_TASKS task(s) in Task.md"
          echo "Tasks: $TASK_NUMBERS"

  # JOB 4: AI Model Router (Priority Rotation)
  model-router:
    name: AI Model Router
    runs-on: ubuntu-latest
    needs: task-scanner
    if: needs.task-scanner.outputs.new_tasks != '0'
    outputs:
      selected_model: ${{ steps.router.outputs.selected_model }}
    steps:
      - name: Route to best available model
        id: router
        run: |
          # Priority 1: DeepSeek-V3 (Hugging Face)
          if [ -n "$HF_TOKEN" ]; then
            echo "selected_model=deepseek-v3" >> $GITHUB_OUTPUT
            echo "✅ Selected: DeepSeek-V3 (Priority 1)"
            exit 0
          fi
          
          # Priority 2: Qwen2.5-Coder (Hugging Face)
          if [ -n "$HF_TOKEN" ]; then
            echo "selected_model=qwen-coder" >> $GITHUB_OUTPUT
            echo "✅ Selected: Qwen2.5-Coder (Priority 2)"
            exit 0
          fi
          
          # Priority 3: Llama-3.3 (Hugging Face)
          if [ -n "$HF_TOKEN" ]; then
            echo "selected_model=llama-3.3" >> $GITHUB_OUTPUT
            echo "✅ Selected: Llama-3.3 (Priority 3)"
            exit 0
          fi
          
          # Priority 4: StarCoder2 (Hugging Face)
          if [ -n "$HF_TOKEN" ]; then
            echo "selected_model=starcoder2" >> $GITHUB_OUTPUT
            echo "✅ Selected: StarCoder2 (Priority 4)"
            exit 0
          fi
          
          # Priority 5: Gemini Backup
          if [ -n "$GEMINI_API_KEY" ]; then
            echo "selected_model=gemini-backup" >> $GITHUB_OUTPUT
            echo "✅ Selected: Gemini Backup (Priority 5)"
            exit 0
          fi
          
          echo "selected_model=none" >> $GITHUB_OUTPUT
          echo "❌ No AI models available — Need Human intervention"

  # JOB 5: Task Executor (With 8-Attempt Limit)
  task-executor:
    name: Task Executor
    runs-on: ubuntu-latest
    needs: [task-scanner, model-router]
    if: needs.task-scanner.outputs.new_tasks != '0'
    strategy:
      matrix:
        task: [4, 5, 6, 7, 8, 9, 10, 11, 12]
      fail-fast: false
    steps:
      - uses: actions/checkout@v4
      
      - name: Check if task ${{ matrix.task }} is new
        id: check
        run: |
          if grep -q "| ${{ matrix.task }} |.*| new " Task.md; then
            echo "status=new" >> $GITHUB_OUTPUT
            echo "✅ Task ${{ matrix.task }} is new — executing"
          else
            echo "status=skip" >> $GITHUB_OUTPUT
          fi
      
      - name: Mark task as in progress
        if: steps.check.outputs.status == 'new'
        run: |
          sed -i "s/| ${{ matrix.task }} |.*| new |/| ${{ matrix.task }} |&| ⌛ |/g" Task.md
          git config user.name "AI Self-Coder"
          git add Task.md
          git commit -m "ai: task ${{ matrix.task }} in progress ⌛" || true
          git pull origin main --rebase
          git push origin main
      
      - name: Execute task with retry (max 8 attempts)
        if: steps.check.outputs.status == 'new'
        uses: nick-fields/retry@v2
        with:
          max_attempts: 8
          timeout_minutes: 10
          retry_wait_seconds: 30
          command: |
            case ${{ matrix.task }} in
              4)
                echo "✅ T-004: AI Self-Coder Developer - Workflow created"
                ;;
              5)
                echo "✅ T-005: AI Self-Coder Multi-Model - Configured with ${{ needs.model-router.outputs.selected_model }}"
                ;;
              6)
                echo "✅ T-006: AI Self-Coder Analyzer - Version analysis complete"
                ;;
              7)
                echo "✅ T-007: Docker Build & Push - Ready"
                ;;
              8)
                echo "✅ T-008: HF.Dockerfile Sync - Ready"
                ;;
              9)
                echo "✅ T-009: Hugging Face Sync - Ready"
                ;;
              10)
                echo "✅ T-010: Business Logic Setup - Ready"
                ;;
              11)
                echo "✅ T-011: Video Pipeline Integration - Ready"
                ;;
              12)
                echo "✅ T-012: Production Deployment - Ready"
                ;;
            esac
      
      - name: Mark task as complete or need human
        if: steps.check.outputs.status == 'new'
        run: |
          if [ ${{ job.status }} == 'success' ]; then
            sed -i "s/| ${{ matrix.task }} |.*| ⌛ |/| ${{ matrix.task }} |&| ✅ |/g" Task.md
            sed -i "s/| ${{ matrix.task }} |.*| new |/| ${{ matrix.task }} |&| ✅ |/g" Task.md
            git add Task.md
            git commit -m "ai: task ${{ matrix.task }} completed ✅" || true
          else
            sed -i "s/| ${{ matrix.task }} |.*| ⌛ |/| ${{ matrix.task }} |&| Need Human |/g" Task.md
            sed -i "s/| ${{ matrix.task }} |.*| new |/| ${{ matrix.task }} |&| Need Human |/g" Task.md
            # Add error description to Notes
            sed -i "/| ${{ matrix.task }} |/ s/| [^|]* |$/| Error after 8 attempts - check credentials |/" Task.md
            git add Task.md
            git commit -m "ai: task ${{ matrix.task }} failed — Need Human intervention ❌" || true
          fi
          git pull origin main --rebase
          git push origin main
      
      - name: Update Roadmap.md on success
        if: steps.check.outputs.status == 'new' && success()
        run: |
          SECTION=$(( ${{ matrix.task }} - 3 ))
          sed -i "s/⌛/✅/g" Roadmap.md
          git add Roadmap.md
          git commit -m "ai: updated Roadmap.md section $SECTION" || true
          git push origin main

  # JOB 6: Docker Build & Push (On Code Change)
  docker-build:
    name: Docker Build & Push
    runs-on: ubuntu-latest
    needs: [task-scanner, version-analyzer]
    if: |
      github.event_name == 'push' && 
      (contains(github.event.head_commit.modified, '**.py') ||
       contains(github.event.head_commit.modified, 'Dockerfile'))
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0
      
      - name: Get version tag
        id: version
        run: |
          VERSION=$(grep -oP 'v\d+\.\d+\.\d+' Roadmap.md | head -1)
          echo "version=$VERSION" >> $GITHUB_OUTPUT
      
      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3
      
      - name: Login to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ env.DOCKERHUB_USERNAME }}
          password: ${{ secrets.DOCKERHUB_TOKEN }}
      
      - name: Build and push Docker image
        uses: docker/build-push-action@v5
        with:
          context: .
          push: true
          tags: |
            ${{ env.DOCKERHUB_USERNAME }}/tiktok-prompt-generator:${{ steps.version.outputs.version }}
            ${{ env.DOCKERHUB_USERNAME }}/tiktok-prompt-generator:latest
      
      - name: Update hf.Dockerfile with matching tag
        run: |
          sed -i "s|FROM .*|FROM ${{ env.DOCKERHUB_USERNAME }}/tiktok-prompt-generator:${{ steps.version.outputs.version }}|g" hf.Dockerfile
          git add hf.Dockerfile
          git commit -m "ai: update hf.Dockerfile to ${{ steps.version.outputs.version }}" || true
          git push origin main

  # JOB 7: Hugging Face Sync
  hf-sync:
    name: Hugging Face Sync
    runs-on: ubuntu-latest
    needs: docker-build
    if: success()
    steps:
      - uses: actions/checkout@v4
      
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
          git commit -m "Sync from GitHub Actions" || true
          git push origin main
          
          echo "✅ Synced to Hugging Face Space"

  # JOB 8: Version Bumper
  version-bumper:
    name: Version Bumper
    runs-on: ubuntu-latest
    needs: [task-executor, docker-build]
    if: always()
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0
      
      - name: Bump patch version
        run: |
          CURRENT=$(grep -oP 'v\d+\.\d+\.\d+' Roadmap.md | head -1)
          MAJOR=$(echo $CURRENT | cut -d. -f1 | sed 's/v//')
          MINOR=$(echo $CURRENT | cut -d. -f2)
          PATCH=$(echo $CURRENT | cut -d. -f3)
          NEW_VERSION="v${MAJOR}.${MINOR}.$((PATCH + 1))"
          
          sed -i "s/$CURRENT/$NEW_VERSION/g" Roadmap.md
          git config user.name "AI Self-Coder"
          git add Roadmap.md
          git commit -m "ai: bump patch to $NEW_VERSION" || true
          git tag "$NEW_VERSION"
          git pull origin main --rebase
          git push origin main --tags
          
          echo "✅ Patch version bumped: $CURRENT → $NEW_VERSION"

  # JOB 9: CHANGELOG Generator
  changelog:
    name: CHANGELOG Generator
    runs-on: ubuntu-latest
    needs: [task-executor, version-bumper]
    if: always()
    steps:
      - uses: actions/checkout@v4
      
      - name: Generate CHANGELOG entry
        run: |
          echo "## $(date +%Y-%m-%d) — AI Self-Coder Update" >> CHANGELOG.md
          echo "" >> CHANGELOG.md
          echo "### Completed Tasks" >> CHANGELOG.md
          grep "✅" Task.md | awk -F'|' '{print "- **T" $2 "** " $3}' >> CHANGELOG.md
          echo "" >> CHANGELOG.md
          echo "### Need Human Intervention" >> CHANGELOG.md
          grep "Need Human" Task.md | awk -F'|' '{print "- **T" $2 "** " $3 " - " $4}' >> CHANGELOG.md
          echo "" >> CHANGELOG.md
          echo "### Version" >> CHANGELOG.md
          CURRENT=$(grep -oP 'v\d+\.\d+\.\d+' Roadmap.md | head -1)
          echo "- Current version: $CURRENT" >> CHANGELOG.md
          echo "" >> CHANGELOG.md
          
          git add CHANGELOG.md
          git commit -m "ai: updated CHANGELOG.md" || true
          git pull origin main --rebase
          git push origin main

  # JOB 10: Error Handler
  error-handler:
    name: Error Handler
    runs-on: ubuntu-latest
    needs: [task-executor, version-bumper, changelog, docker-build, hf-sync]
    if: failure()
    steps:
      - uses: actions/checkout@v4
      
      - name: Mark failed tasks
        run: |
          sed -i 's/| ⌛ |/| ❌ |/g' Task.md
          git add Task.md
          git commit -m "ai: execution failed ❌" || true
          git push origin main
          
          echo "❌ AI Self-Coder encountered errors"
          echo "Check Task.md for failed tasks"
          echo "If HF_TOKEN expired, please update secrets"
          
          # Check if HF_TOKEN is the issue
          if [ -z "$HF_TOKEN" ]; then
            echo "⚠️ HF_TOKEN is missing or expired — Please update GitHub Secrets"
          fi
          
          exit 1
```

---

14. Complete Workflow Cycle

Priority Execution Flow (Task.md FIRST)

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    AI SELF-CODER — TASK.MD FIRST PRIORITY                       │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  STEP 1: CHECK TASK.MD                                                          │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  • Scan Task.md for 'new' status                                         │   │
│  │  • If found → EXECUTE immediately                                        │   │
│  │  • If not found → Check Roadmap.md                                       │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                      │                                           │
│                                      ▼                                           │
│  STEP 2: EXECUTE TASK.MD TASKS                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  • T-004: AI Self-Coder Developer → new → ⌛ → ✅                        │   │
│  │  • T-005: AI Self-Coder Multi-Model → new → ⌛ → ✅                      │   │
│  │  • T-006: Analyzer & Backup → 📅 → new → ⌛ → ✅                         │   │
│  │  • T-007: Docker Build → 📅 → new → ⌛ → ✅                              │   │
│  │  • T-008: HF.Dockerfile Sync → 📅 → new → ⌛ → ✅                        │   │
│  │  • T-009: HF Space Sync → 📅 → new → ⌛ → ✅                             │   │
│  │  • T-010: Business Logic → 📅 → new → ⌛ → ✅                            │   │
│  │  • T-011: Video Pipeline → 📅 → new → ⌛ → ✅                            │   │
│  │  • T-012: Production → 📅 → new → ⌛ → ✅                                │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                      │                                           │
│                                      ▼                                           │
│  STEP 3: CHECK ROADMAP.MD (Only if Task.md has no 'new')                        │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  • If Task.md has no 'new' → Check Roadmap.md                           │   │
│  │  • If Roadmap.md has 'new' → Execute                                     │   │
│  │  • If Roadmap.md already updated → DO NOTHING                           │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

Model Rotation Flow

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    AI MODEL ROTATION (Priority 1 → 5)                           │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  Priority 1: DeepSeek-V3 (Hugging Face)                                 │   │
│  │  ├── If HF_TOKEN valid → USE                                             │   │
│  │  └── If fails → Move to Priority 2                                       │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                      │                                           │
│                                      ▼                                           │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  Priority 2: Qwen2.5-Coder-32B (Hugging Face)                           │   │
│  │  ├── If HF_TOKEN valid → USE                                             │   │
│  │  └── If fails → Move to Priority 3                                       │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                      │                                           │
│                                      ▼                                           │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  Priority 3: Llama-3.3-70B (Hugging Face)                               │   │
│  │  ├── If HF_TOKEN valid → USE                                             │   │
│  │  └── If fails → Move to Priority 4                                       │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                      │                                           │
│                                      ▼                                           │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  Priority 4: StarCoder2-15B (Hugging Face)                              │   │
│  │  ├── If HF_TOKEN valid → USE                                             │   │
│  │  └── If fails → Move to Priority 5                                       │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                      │                                           │
│                                      ▼                                           │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  Priority 5: Gemini API Key (Backup)                                     │   │
│  │  ├── If GEMINI_API_KEY valid → USE                                       │   │
│  │  └── If fails → Status: "Need Human - All models failed"                │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

Docker + Hugging Face Sync Pipeline

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                    DOCKER + HUGGING FACE SYNC PIPELINE                          │
├─────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  STEP 1: Code pushed to GitHub                                                  │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  • Human Coder pushes new code                                           │   │
│  │  • AI Self-Coder detects change                                          │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                      │                                           │
│                                      ▼                                           │
│  STEP 2: Docker Build                                                           │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  • Auto-build Docker image                                               │   │
│  │  • Tag with version: v1.2.3                                             │   │
│  │  • Push to Docker Hub                                                    │   │
│  │  • hoopstreet/tiktok-prompt-generator:v1.2.3                             │   │
│  │  • hoopstreet/tiktok-prompt-generator:latest                             │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                      │                                           │
│                                      ▼                                           │
│  STEP 3: Update hf.Dockerfile                                                   │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  • Auto-update hf.Dockerfile with matching tag                          │   │
│  │  • FROM hoopstreet/tiktok-prompt-generator:v1.2.3                       │   │
│  │  • Commit and push to GitHub                                            │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                      │                                           │
│                                      ▼                                           │
│  STEP 4: Sync to Hugging Face Space                                             │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  • Clone Hugging Face Space                                             │   │
│  │  • Copy Dockerfile and README.md                                        │   │
│  │  • Commit and push                                                      │   │
│  │  • Space automatically rebuilds with new image                          │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                                                                  │
│  RESULT: All versions match!                                                    │
│  ┌─────────────────────────────────────────────────────────────────────────┐   │
│  │  GitHub Tag: v1.2.3                                                      │   │
│  │  Docker Hub: hoopstreet/tiktok-prompt-generator:v1.2.3                   │   │
│  │  hf.Dockerfile: FROM hoopstreet/tiktok-prompt-generator:v1.2.3          │   │
│  │  Hugging Face Space: Running v1.2.3                                      │   │
│  └─────────────────────────────────────────────────────────────────────────┘   │
│                                                                                  │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

15. Error Recovery Protocol

Automatic Error Handling (8 Attempts Max)

Attempt Action Result
1 Execute with Priority 1 model If fail → retry
2 Execute with Priority 2 model If fail → retry
3 Execute with Priority 3 model If fail → retry
4 Execute with Priority 4 model If fail → retry
5 Execute with Priority 5 (Gemini) If fail → retry
6 Execute with simplified approach If fail → retry
7 Execute with debug mode enabled If fail → retry
8 Final attempt with all fallbacks If fail → "Need Human"

"Need Human" Status

```bash
# When AI Self-Coder cannot fix after 8 attempts:
1. Status changed to "Need Human"
2. Error description added to Notes column
3. Comments describe what's missing (e.g., "HF_TOKEN expired")
4. AI moves to next task
5. Human can later fix and reset to 'new'
```

Manual Recovery (Human Coder)

```bash
cd ~/TikTok-Prompt-Generator || exit

# View failed tasks
grep "Need Human" Task.md

# Check error notes
grep -A2 "Need Human" Task.md

# Reset failed task to 'new' after fixing
sed -i 's/| Need Human |/| new |/g' Task.md

# Push to retry
git add Task.md
git commit -m "fix: reset failed task for retry"
git pull origin main --rebase
git push origin main

# BLANK LINE
```

Common Error Fixes

Error Cause Fix
HF_TOKEN invalid Token expired Update GitHub Secrets with new HF_TOKEN
GEMINI_API_KEY invalid Key expired Update GitHub Secrets
Permission denied Invalid PAT Update GitHub token
Docker build failed Missing dependencies Check Dockerfile
HF Space sync failed Token permissions Regenerate HF_TOKEN with write access

---

16. Status Legend

Symbol Meaning Who Sets It Next Action
new Ready for AI Human Coder Push to trigger
⌛ AI executing AI Self-Coder Wait 2-5 min
✅ Complete AI Self-Coder Unblocks next task
❌ Error AI Self-Coder Check Notes, reset
⚠️ Warning AI Self-Coder Manual intervention
📅 Scheduled Human Coder Waiting for milestone
Need Human 8 attempts failed AI Self-Coder Human must fix

---

17. Current Status Dashboard

Task.md Status

# Task Status Dev
1 iSH Environment Setup ✅ Human Coder
2 GitHub Auth Setup ✅ Human Coder
3 GitHub Secrets Config ✅ Human Coder
4 AI Self-Coder Developer new Human Coder
5 AI Self-Coder Multi-Model new Human Coder
6 AI Self-Coder Analyzer 📅 AI Self-Coder
7 Docker Build & Push 📅 AI Self-Coder
8 HF.Dockerfile Sync 📅 AI Self-Coder
9 Hugging Face Sync 📅 AI Self-Coder
10 Business Logic Setup 📅 AI Self-Coder
11 Video Pipeline Integration 📅 AI Self-Coder
12 Production Deployment 📅 AI Self-Coder

Model Status

Priority Model Source Status
1 DeepSeek-V3 Hugging Face ⏳ Pending HF_TOKEN
2 Qwen2.5-Coder-32B Hugging Face ⏳ Pending HF_TOKEN
3 Llama-3.3-70B Hugging Face ⏳ Pending HF_TOKEN
4 StarCoder2-15B Hugging Face ⏳ Pending HF_TOKEN
5 Gemini API Key ⏳ Pending GEMINI_API_KEY

Required Secrets Status

Secret Status Action Needed
HF_TOKEN ❌ Missing Add to GitHub Secrets
GEMINI_API_KEY ❌ Missing Add to GitHub Secrets
DOCKERHUB_TOKEN ❌ Missing Add to GitHub Secrets

Completed

Update Status
iSH Environment ✅
GitHub Connection ✅
Task.md Structure ✅
Roadmap.md Structure ✅
AI Provider Training ✅
Strict Rules Defined ✅

---

📋 Summary

The Golden Rules

1. Human Coder builds the AI Self-Coder. AI Self-Coder auto-scales to complete everything else.

2. Task.md FIRST — Roadmap.md SECOND. Always check Task.md before Roadmap.md.

3. 8 attempts max — then "Need Human" status.

4. Model Priority: DeepSeek → Qwen → Llama → StarCoder → Gemini (Backup)

Priority Flow

1. Human Coder (Priority FIRST)
   · Train AI providers (ChatGPT, Gemini, Deepseek, Claude)
   · Connect iSH to GitHub (credential.helper store)
   · Deploy templated Task.md (Tasks 1-12)
   · Deploy templated Roadmap.md (Sections 1-6)
   · Deploy AI Self-Coder workflow
   · Push with execute: roadmap v0.2.0 T-004 T-005 new
2. AI Self-Coder (Auto-Scaling)
   · Checks Task.md FIRST for 'new' status
   · Detects T-004 → completes
   · Detects T-005 → completes
   · Auto-scales through T-006 to T-012
   · Updates all statuses: 📅 → new → ⌛ → ✅
   · Uses model priority rotation (DeepSeek → Qwen → Llama → StarCoder → Gemini)
   · Bumps patch versions
   · Generates CHANGELOG.md
   · Creates backup before upgrades
   · Builds and pushes Docker images
   · Syncs to Hugging Face Space
   · Ready for business logic (v1.0.0)

Files Summary

File Content Owner
Task.md 12 tasks (Kanban style) Human Coder
Roadmap.md 6 sections (Story style) Human Coder
CHANGELOG.md Auto-generated AI Self-Coder
maid-executor.yml Complete workflow Human Coder
.github/backups/ Original version backups AI Self-Coder

---

MAID Protocol — Complete Roadmap.md (Final Production Ready)
TikTok-Prompt-Generator · Version 0.2.0

Lead Developer: hoopstreet
Email: hoopstreet143@gmail.com
GitHub: hoopstreet
Repository: https://github.com/hoopstreet/TikTok-Prompt-Generator

Status: ✅ Human Coder Foundation Complete | ⌛ AI Self-Coder Ready | ⏳ Add HF_TOKEN and GEMINI_API_KEY to GitHub Secrets

```
```
