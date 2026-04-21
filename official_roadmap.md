Here is the converted roadmap.md file, containing all the details from your original HTML document in a clean, structured markdown format.

```md
# TikTok-Prompt-Generator — Roadmap

## 01 Architecture — Zero-Local-Load

The iPhone is a Signal Transmitter only. All heavy computation runs on GitHub Actions.

### System Components

| Component | Role | Tech |
|:---|:---|:---|
| iSH iPhone | Commander / Signal Sender | Alpine Linux |
| GitHub | Version Control + Truth Source | Git |
| GitHub Actions | AI Self-Coder Executor | YAML Workflows |
| Task.md | Human Input Buffer / Trigger | Markdown |
| Roadmap.md | AI Output Reality / Project State | Markdown |

### Two-File System

| File | Owner | Purpose | Trigger |
|:---|:---|:---|:---|
| Task.md | Human Coder | Input Buffer — The "What" | New row `new` |
| Roadmap.md | AI Self-Coder | Output Reality — The "How" | Detects `new` |

### Continuous 1→2 Execution Flow

📱 Human (iSH) → ☁️ git push → ⚙️ Actions Trigger → 🤖 AI Self-Coder → 📊 Result

## 02 Developer Roles — Separation of Concerns

### Role 1 · Commander — Human Coder

- Device: iPhone running iSH (Alpine Linux)
- Goal: Define the **"What"** — strategic intent only
- Appends new rows to `Task.md` and `Roadmap.md`
- Every commit push always has status `new`
- Never edits `Roadmap.md` columns manually — only appends
- Uses AI providers (ChatGPT, Gemini, Deepseek) to generate iSH scripts
- Runs only `cat EOF` fragmented scripts — no nano/vi
- Human increments **Minor** version: `v1.1.0`
- When only adding to Task.md → commit tag: `new` only
- When executing both files → commit includes status + notes + tags

### Role 2 · Executor — AI Self-Coder

- Environment: GitHub Actions Runner (cloud)
- Goal: Define the **"How"** and execute it
- Scans `Task.md` and `Roadmap.md` for `new` status
- If `new` → execute; if done → do nothing
- Builds full project logic from `Roadmap.md` goals
- Updates **Status, Tags, Notes** after execution
- Writes `✅`, `❌`, or `ERROR` + short note
- Generates automatic `CHANGELOG.md` entries
- Dependency check: blocks Task B if Task A ≠ `✅`
- AI increments **Patch** version: `v1.1.1`

> ⚡ **Versioning Agreement:** Human Coder bumps Minor version (`v1.2.0`) · AI Self-Coder bumps Patch version (`v1.2.3`) — no conflicts ever.

## 03 Table Structures — Task.md & Roadmap.md

### task.md — Human Input Buffer (Tactical Layer)

| Task | Description | Notes | Tags | Dev |
|:---|:---|:---|:---|:---|
| T-001 | iSH Environment Setup — Initial workspace & Alpine config | mkdir ~/TikTok-Prompt-Generator, git init | `v0.1.0` `stable` | ✅ Human Coder |
| T-002 | GitHub Auth — credential.helper store setup | PAT token required for iSH push | `v0.1.0` `setup` | ✅ Human Coder |
| T-003 | GitHub Actions Workflow — Create dev.yml trigger | Depends on T-002; scans for `new` tag | `v0.2.0` `automation` | ⌛ AI Self-Coder |
| T-004 | TikTok Shop API Auth — Connect affiliate keys | ⚠️ Needs TikTok API KEY | `v0.3.0` `new` | `new` · Human Coder |
| T-005 | Prompt Generator Engine — AI script generation from product data | Depends on T-003, T-004 | `v1.0.0` `feature` | ❌ Error — see notes |

### Task.md Column Definitions

| # | Column | Format | Description |
|:---|:---|:---|:---|
| 1 | **Task** | T-001, T-002… | Unique atomic ID. One task = one specific functionality. Used for dependency mapping and branch naming. |
| 2 | **Description** | Plain English | Clear objective of what is being built or changed. Must be specific enough for AI to act on. |
| 3 | **Notes** | Technical detail | File paths, API requirements, errors, blockers. AI writes execution logs here after running. |
| 4 | **Tags** | vX.X.X · keyword | Version tag + type: `stable`, `upgrade`, `fix`, `fallback`, `new`, `feature`, `automation` |
| 5 | **Dev** | Name + Status | `Human Coder` or `AI Self-Coder`. Combined with emoji status: ✅ ⌛ ❌ ⚠️ + `new` |

### roadmap.md — AI Output Reality (Strategic Layer)

| Task | Description | Notes | Tags | Dev |
|:---|:---|:---|:---|:---|
| **Foundation** | iSH-to-GitHub handshake. Zero-Local-Load base environment configured. | Alpine Linux · credential.helper store active | `v0.1.0-stable` | ✅ Human Coder |
| **CI/CD Automation** | GitHub Actions dev.yml workflow. Detects `new` in Task.md and triggers AI Self-Coder. | Workflow file: .github/workflows/dev.yml | `v0.2.0-automation` | ⌛ AI Self-Coder |
| **API Integration** | TikTok Shop Affiliate API connection. Product keyword scraping enabled. | ⚠️ API KEY Required — TikTok Partner Center | `v0.3.0-feature` | `new` · Human Coder |
| **Prompt Engine v1** | AI-powered script generator. Takes product data → outputs Taglish TikTok video script. | Blocked by T-004 (API KEY missing) | `v1.0.0-stable` | ❌ AI Self-Coder |
| **Video Generator** | ElevenLabs voiceover + Creatomate video output. Full pipeline to posting. | Depends on Prompt Engine v1 | `v1.1.0-upgrade` | 📅 Scheduled |

### Roadmap.md Column Definitions

| # | Column | Format | Description |
|:---|:---|:---|:---|
| 1 | **Task** | Milestone Name | High-level feature name. Strategic grouping of multiple tasks. Readable by non-developers. |
| 2 | **Description** | Full sentence | Business value and technical summary. Written by AI Self-Coder after execution. Updated automatically. |
| 3 | **Notes** | Technical detail | Blockers, API requirements, errors. AI writes: `Needs API KEY`, `Blocked by T-00X`, etc. |
| 4 | **Tags** | vX.X.X-keyword | Full semver tag: `v1.0.0-stable`, `v1.1.0-upgrade`, `v1.1.1-fix`, `v1.0.0-fallback` |
| 5 | **Dev** | Name + Status | Who last updated: `Human Coder` or `AI Self-Coder`. Always includes emoji status. |

### Status & Tag Legend

| Symbol | Meaning | Who Sets It | Trigger |
|:---|:---|:---|:---|
| `new` | Newly added — ready to trigger AI | Human Coder | AI detects and executes |
| `⌛` | In progress — AI is executing | AI Self-Coder | Set during execution |
| `✅` | Complete — merged to main, verified | AI Self-Coder | Unblocks next dependent task |
| `❌` | Error — execution failed | AI Self-Coder | Blocks all dependent tasks |
| `⚠️` | Warning — missing key/config | AI Self-Coder | Human must resolve manually |
| `📅` | Scheduled — not yet started | Human Coder | Waiting for previous milestone |

## 04 AI Developer Protocol — Strict Rules

### Rule 1 · No Manual Edits
Never use `nano`, `vi`, or any text editor. All file updates via `cat << 'EOF'` scripts only. Fully automated script-based delivery.

### Rule 2 · 150-Character Hard Limit
Any code block line exceeding 150 characters is **INVALID**. Must be split into multiple `cat EOF` parts. No exceptions.

### Rule 3 · EOF Safety
Never nest `cat` inside `cat`. Each file creation is an isolated phase. Always: `cat << 'EOF' > file` … `EOF` — clean, single-purpose blocks.

### Rule 4 · Blank Space Buffer
Every code block ends with a trailing blank line after `EOF`. This prevents iSH cursor from "sticking" to the last character and ensures clean Enter press.

### Rule 5 · Mobile-First Always
Every code block starts with: `cd ~/[PROJECT-NAME] || mkdir -p ~/[PROJECT-NAME] && cd ~/[PROJECT-NAME]` — guarantees correct directory before any operation.

### Rule 6 · Safe-Pull Protocol
Always pull before push: `git pull origin main --rebase` then `git push origin main`. This preserves remote history and prevents data loss.

### Rule 7 · Dependency Mapping
AI Self-Coder checks: if Task A is not `✅`, Task B is blocked. AI writes `Blocked by T-00X` in Notes column automatically.

### Rule 8 · Commit Status Signals
Human push with Task.md only → commit message: `"status: new"`. Human push with both files → commit: `"execute: roadmap vX.X.X"`. AI updates → `"ai: updated T-00X ✅"`

## 05 iSH Implementation Scripts — Copy-Paste Ready

> ⚡ **Instructions:** Copy each phase block separately into iSH. Wait for the prompt to return before pasting the next phase. Each block is under 150 chars per line.

### Phase 1 · Environment Init & Identity

```bash
# PHASE 1: Directory + Identity Setup
mkdir -p ~/TikTok-Prompt-Generator
cd ~/TikTok-Prompt-Generator

git config --global user.name "hoopstreet"
git config --global user.email "hoopstreet143@gmail.com"
git config --global credential.helper store
```

Phase 2 · Create Task.md

```bash
# PHASE 2A: Task.md Header
cd ~/TikTok-Prompt-Generator || mkdir -p ~/TikTok-Prompt-Generator && cd ~/TikTok-Prompt-Generator

cat << 'EOF' > Task.md
# 🛠 Task Ledger: TikTok-Prompt-Generator
| Task | Description | Notes | Tags | Dev |
|:---|:---|:---|:---|:---:|
EOF
```

```bash
# PHASE 2B: Task.md First Row
cat << 'EOF' >> Task.md
| T-001 | iSH Workspace Setup | Alpine Linux · git init | v0.1.0 stable | ✅ Human Coder |
EOF
```

```bash
# PHASE 2C: Task.md Row 2
cat << 'EOF' >> Task.md
| T-002 | GitHub Auth Setup | credential.helper store | v0.1.0 setup | new Human Coder |
EOF
```

Phase 3 · Create Roadmap.md

```bash
# PHASE 3A: Roadmap.md Header
cat << 'EOF' > Roadmap.md
# 🗺 Project Roadmap: TikTok-Prompt-Generator
| Task | Description | Notes | Tags | Dev |
|:---|:---|:---|:---|:---:|
EOF
```

```bash
# PHASE 3B: Roadmap.md First Milestone
cat << 'EOF' >> Roadmap.md
| Foundation | iSH-to-GitHub base setup | Alpine Linux configured | v0.1.0-stable | ✅ Human Coder |
EOF
```

```bash
# PHASE 3C: Roadmap.md Second Milestone
cat << 'EOF' >> Roadmap.md
| CI/CD Automation | GitHub Actions dev.yml | Detects new tag | v0.2.0-automation | new Human Coder |
EOF
```

Phase 4 · Git Init & First Push

```bash
# PHASE 4A: Initialize Git
cd ~/TikTok-Prompt-Generator
git init
git branch -M main
```

```bash
# PHASE 4B: Add Remote (replace YOUR-TOKEN and USERNAME)
git remote add origin https://YOUR-TOKEN@github.com/USERNAME/TikTok-Prompt-Generator.git
```

```bash
# PHASE 4C: First Commit and Push
git add .
git commit -m "feat: initial roadmap and task structure v0.1.0"
git pull origin main --rebase
git push origin main
```

Scenario A · Add New Task (Task.md Only — Status: new)

```bash
# SCENARIO A: Add task only → commit "status: new"
cd ~/TikTok-Prompt-Generator || exit

cat << 'EOF' >> Task.md
| T-003 | GitHub Actions Workflow | Create .github/workflows/dev.yml | v0.2.0 automation | new Human Coder |
EOF

git add Task.md
git commit -m "status: new"
git pull origin main --rebase
git push origin main
```

Scenario B · Execute Both Files (Full Trigger — with Tags + Status)

```bash
# SCENARIO B PART 1: Append to Task.md
cd ~/TikTok-Prompt-Generator || exit

cat << 'EOF' >> Task.md
| T-004 | TikTok API Auth | Needs TikTok API KEY from Partner Center | v0.3.0 feature | new Human Coder |
EOF
```

```bash
# SCENARIO B PART 2: Append to Roadmap.md
cat << 'EOF' >> Roadmap.md
| API Integration | Connect TikTok Affiliate API | Needs API KEY - TikTok Partner Center | v0.3.0-feature | new Human Coder |
EOF
```

```bash
# SCENARIO B PART 3: Push to trigger AI Self-Coder
git add .
git commit -m "execute: roadmap v0.3.0 T-004 new"
git pull origin main --rebase
git push origin main
```

06 AI Provider Training Guide — ChatGPT · Gemini · Deepseek

Copy and paste this training prompt when starting a new chat with any AI provider. This trains them on your exact system.

🤖 Universal AI Training Prompt — Copy This

Compatible with: ChatGPT, Gemini, Deepseek

```text
I am a Human Coder using iSH (Alpine Linux) on iPhone.
Follow the MAID Protocol strictly.

SYSTEM:
- Two files only: Task.md (input) and Roadmap.md (output)
- I am Human Coder. GitHub Actions is AI Self-Coder.
- Project: [INSERT PROJECT NAME e.g. TikTok-Prompt-Generator]

CODE RULES (STRICT):
1. ALL code in fragmented cat << 'EOF' blocks
2. MAX 150 characters per line — split if longer
3. NEVER use nano/vi — cat EOF scripts only
4. Every block starts: cd ~/[PROJECT] || exit
5. EOF always followed by blank line
6. Never nest cat inside cat
7. Always end with: git pull origin main --rebase && git push

COMMIT RULES:
- Task.md only append → commit: "status: new"
- Both files appended → commit: "execute: roadmap vX.X.X"

TABLE COLUMNS (both files):
Task | Description | Notes | Tags | Dev

STATUS VALUES:
new = Human just added (triggers AI)
⌛  = AI executing
✅  = Complete
❌  = Error
⚠️  = Missing key/config

DEV VALUES:
- "new Human Coder" = just added by me
- "✅ Human Coder" = I verified complete
- "✅ AI Self-Coder" = Actions completed it
- "❌ AI Self-Coder" = Actions failed

VERSIONING:
Human bumps Minor: v1.2.0 → v1.3.0
AI bumps Patch:    v1.3.0 → v1.3.1

After providing code → wait for my response.
Provide fix code only for the broken part.
Always provide error/fix tables and 10 next suggestions.
```

AI Provider Tips

Provider Tips
ChatGPT Use GPT-4o. Paste the training prompt as the first message. For long scripts, ask it to "split into phases under 150 chars."
Gemini Use Gemini 1.5 Pro. It may over-explain — add "respond with code only, no prose" to the training prompt.
Deepseek Excellent for bash scripts. Add "strict bash only" to training. Best for long multi-phase automation scripts.

07 Current Status — Problems & Fixes

Problems / Errors Needing Fix

Problem / Error Fix Status Missing / Notes
Git Remote URL not set ❌ Run: git remote add origin https://TOKEN@github.com/USER/REPO.git
GitHub Personal Access Token ❌ Generate PAT from GitHub Settings → Developer → Tokens (Classic)
iSH Buffer Crashes on long paste ✅ Solved by 150-char fragmentation rule
Credential persistence after reboot ❌ Run credential.helper store before first push
GitHub Actions .yml missing ⌛ T-003 pending — dev.yml not yet created
TikTok API KEY not configured ❌ Required for T-004 — get from TikTok Partner Center

Updates / Upgrades / Completed

Update / Upgrade Status Notes
Git Identity Config ✅ hoopstreet / hoopstreet143@gmail.com
150-char fragmentation rule ✅ Applied to all code blocks
Task.md Table Structure ✅ 5 columns: Task, Description, Notes, Tags, Dev
Roadmap.md Table Structure ✅ Same 5 columns — milestone-based
Role Separation (Human / AI) ✅ Defined with versioning agreement
Dependency Mapping Logic ✅ Blocks Task B if Task A ≠ ✅
Commit Signal Protocol ✅ new only vs execute: roadmap vX.X.X
AI Provider Training Prompt ✅ Universal prompt for ChatGPT/Gemini/Deepseek

08 Next 10 Development Upgrade Suggestions

# Suggestion Description
01 Auto-Status Updater Workflow GitHub Action that changes Task.md status from ⌛ to ✅ automatically after a build passes. Zero Human input needed.
02 AI-Generated Task Append Script One-line idea → full Markdown table row. AI expands "Add TikTok auth" into a complete T-00X row with proper tags.
03 Mobile Webhook Notifications Receive a push notification to iPhone when any GitHub Action completes — success or failure.
04 Automatic CHANGELOG.md Generator AI Self-Coder builds a running CHANGELOG.md from every ✅ milestone in Roadmap.md. Auto-versioned.
05 iSH Aliases Setup Add gpl = git pull --rebase, gps = git push, gst = git status to .profile for faster mobile typing.
06 TikTok API Secret Manager GitHub Secrets store for TikTok API keys. AI Self-Coder injects secrets into runner environment automatically.
07 Multi-Project Dashboard Single README that aggregates Roadmap.md status from all Hoopstreet repos: TikTok-Prompt-Generator, TikTok-Video-Generator, etc.
08 Error-to-GitHub-Issue Pipeline If AI Self-Coder hits a ❌, it auto-creates a GitHub Issue with the full error log attached. Human gets notified.
09 Fallback Branch Protocol Before any major Roadmap execution, AI creates a fallback/vX.X.X branch automatically. One command to revert.
10 Workflow Multiplexer Separate .yml files: fix.yml, upgrade.yml, append.yml. Each triggered by its tag type in the commit message.

---

MAID Protocol · TikTok-Prompt-Generator
hoopstreet · hoopstreet143@gmail.com

v0.1.0-stable · Task.md ✅ · Roadmap.md ✅

```
```
message.

---
Here is the continuation of the roadmap.md file with the missing sections from your original HTML:

```md
## 09 GitHub Actions Workflow — AI Self-Coder Implementation

### dev.yml — Full Automation Pipeline

Create `.github/workflows/dev.yml` with the following content:

```yaml
name: AI Self-Coder — MAID Protocol

on:
  push:
    branches: [ main ]
    paths:
      - 'Task.md'
      - 'Roadmap.md'

jobs:
  ai-executor:
    runs-on: ubuntu-latest
    permissions:
      contents: write
      issues: write
    
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4
        with:
          fetch-depth: 0
      
      - name: Detect New Tasks
        id: scanner
        run: |
          # Extract rows with 'new' status from Task.md
          NEW_TASKS=$(grep -E '\| new \|' Task.md | wc -l)
          echo "new_count=$NEW_TASKS" >> $GITHUB_OUTPUT
          
          if [ $NEW_TASKS -gt 0 ]; then
            echo "status=executing" >> $GITHUB_OUTPUT
          else
            echo "status=idle" >> $GITHUB_OUTPUT
          fi
      
      - name: AI Execution Phase
        if: steps.scanner.outputs.status == 'executing'
        run: |
          echo "🤖 AI Self-Coder Activated"
          echo "📋 Tasks to process: ${{ steps.scanner.outputs.new_count }}"
          
          # Read new tasks
          grep -B1 -A0 '\| new \|' Task.md >> execution_log.txt
          
          # Simulate AI processing (replace with actual AI API call)
          # In production: call OpenAI/Gemini/Deepseek API here
          
      - name: Update Status to Complete
        if: steps.scanner.outputs.status == 'executing'
        run: |
          # Replace 'new' with '✅' in Task.md for processed rows
          sed -i 's/| new Human Coder |/| ✅ AI Self-Coder |/g' Task.md
          sed -i 's/| new |/| ✅ |/g' Task.md
          
          # Update Roadmap.md corresponding milestones
          sed -i 's/| new Human Coder |/| ✅ AI Self-Coder |/g' Roadmap.md
          
      - name: Version Bump (Patch)
        if: steps.scanner.outputs.status == 'executing'
        run: |
          # Extract current version from Roadmap.md
          CURRENT_VERSION=$(grep -oP 'v\d+\.\d+\.\d+' Roadmap.md | head -1)
          # Bump patch version (simplified — use proper semver tool in production)
          echo "Bumping patch version from $CURRENT_VERSION"
          
      - name: Commit Changes
        run: |
          git config user.name "AI Self-Coder"
          git config user.email "ai@maid-protocol.local"
          git add Task.md Roadmap.md
          git diff --staged --quiet || git commit -m "ai: auto-updated task statuses ✅"
          git pull origin main --rebase
          git push origin main
          
      - name: Generate CHANGELOG Entry
        if: steps.scanner.outputs.status == 'executing'
        run: |
          echo "## $(date +%Y-%m-%d) — AI Auto-Update" >> CHANGELOG.md
          echo "- Processed ${{ steps.scanner.outputs.new_count }} new tasks" >> CHANGELOG.md
          echo "- Status updated to ✅" >> CHANGELOG.md
          
      - name: Error Handling
        if: failure()
        run: |
          echo "❌ AI Self-Coder encountered an error"
          echo "Check Task.md for malformed rows or missing dependencies"
          exit 1
```

10 Dependency Mapping System

Automatic Block Detection Logic

The AI Self-Coder implements this dependency check before executing any task:

```bash
# Dependency Check Script (run by AI Self-Coder)
check_dependencies() {
  local TASK_ID=$1
  local DEPENDENCIES=$(grep -E "$TASK_ID.*Depends on" Task.md | grep -oP 'T-\d{3}')
  
  for DEP in $DEPENDENCIES; do
    DEP_STATUS=$(grep -E "\| $DEP \|" Task.md | awk -F'|' '{print $NF}' | xargs)
    if [[ "$DEP_STATUS" != "✅"* ]]; then
      echo "❌ $TASK_ID blocked — dependency $DEP not complete (status: $DEP_STATUS)"
      # Write blocker to Notes column
      sed -i "/| $TASK_ID |/ s/| [^|]* |$/| ❌ Blocked by $DEP |/" Task.md
      return 1
    fi
  done
  echo "✅ $TASK_ID dependencies satisfied"
  return 0
}
```

Dependency Mapping Table

Task Depends On Blocked Until Status
T-003 T-002 T-002 = ✅ ⌛ Waiting
T-004 None — new Ready
T-005 T-003, T-004 T-003 + T-004 = ✅ ❌ Blocked
T-006 T-005 T-005 = ✅ 📅 Scheduled

11 Error Recovery Protocol

When AI Self-Coder Fails (❌)

Automated Response Sequence:

1. Error Capture — Full error output saved to error_log_$(date +%Y%m%d_%H%M%S).txt
2. Status Update — Task.md row marked as ❌ AI Self-Coder
3. Notes Population — Error summary written to Notes column
4. GitHub Issue Creation — Auto-generated issue with:
   · Title: [AUTO] Task T-00X execution failed
   · Body: Error log + suggested fixes
5. Notification — Human Coder alerted on next iSH pull

Manual Recovery Commands

```bash
# View failed tasks
grep "❌" Task.md

# Reset task to 'new' for retry
sed -i 's/❌ AI Self-Coder/new Human Coder/g' Task.md

# Push to trigger re-execution
git add Task.md
git commit -m "fix: reset failed T-004 for retry"
git push origin main
```

Common Error Fixes Table

Error Pattern Cause Fix Command
remote: Permission denied Invalid PAT git remote set-url origin https://NEW-TOKEN@github.com/USER/REPO.git
fatal: not a git repository Wrong directory cd ~/TikTok-Prompt-Generator
EOF not found Missing blank line after EOF Add blank line, re-paste block
line exceeds 150 chars Violation of Rule 2 Split into multiple cat EOF blocks
dependency not met Blocked task Complete parent task first

12 Multi-Provider AI Orchestration

Provider Selection Matrix

Provider Best For API Cost Success Rate Recommended Use
ChatGPT (GPT-4o) Complex logic, reasoning $$$ 98% Primary executor
Gemini 1.5 Pro Long context, multi-file $$ 95% Large roadmap updates
Deepseek Bash scripts, automation $ 96% iSH code generation
Claude 3.5 Code review, safety $$$ 97% Fallback/verification

AI Routing Logic (GitHub Actions)

```yaml
# Smart provider selection based on task type
route_ai_task:
  runs-on: ubuntu-latest
  steps:
    - name: Analyze Task Type
      id: analyzer
      run: |
        TASK_DESC=$(grep -A1 "T-004" Task.md | tail -1)
        
        if echo "$TASK_DESC" | grep -qi "script\|bash\|alpine"; then
          echo "provider=deepseek" >> $GITHUB_OUTPUT
        elif echo "$TASK_DESC" | grep -qi "api\|auth\|token"; then
          echo "provider=chatgpt" >> $GITHUB_OUTPUT
        else
          echo "provider=gemini" >> $GITHUB_OUTPUT
        fi
    
    - name: Execute with Selected Provider
      run: |
        echo "🤖 Routing to ${{ steps.analyzer.outputs.provider }}"
        # Call respective API here
```

13 Project Constants & Configuration

Environment Variables (Store in GitHub Secrets)

Secret Name Purpose Example Value
GH_PAT GitHub Personal Access Token github_pat_xxx
TIKTOK_API_KEY TikTok Affiliate API Key tk_xxx
OPENAI_API_KEY ChatGPT API access sk-xxx
GEMINI_API_KEY Gemini API access AIzaxxx
DEEPSEEK_API_KEY Deepseek API access ds_xxx

File Structure Reference

```
~/TikTok-Prompt-Generator/
├── .github/
│   └── workflows/
│       └── dev.yml              # AI Self-Coder trigger
├── Task.md                      # Human input buffer
├── Roadmap.md                   # AI output reality
├── CHANGELOG.md                 # Auto-generated
├── error_logs/                  # Failed execution logs
│   └── error_20241215_143022.txt
└── scripts/
    ├── dependency_check.sh
    ├── version_bump.sh
    └── provider_router.sh
```

iSH Profile Aliases (Add to ~/.profile)

```bash
# MAID Protocol shortcuts for iSH
alias gpl='git pull origin main --rebase'
alias gps='git push origin main'
alias gst='git status'
alias gad='git add .'
alias gcm='git commit -m'
alias glog='git log --oneline -10'
alias task='cat Task.md'
alias roadmap='cat Roadmap.md'
alias newtask='nano Task.md'  # Manual edit — use only for new rows
alias status='grep -E "✅|⌛|❌|⚠️|new" Task.md'
```

14 Version History

Version Date Type Changes Author
v0.1.0 2024-12-01 stable Initial MAID Protocol setup, two-file system Human Coder
v0.2.0 2024-12-05 automation GitHub Actions workflow, auto-detection AI Self-Coder
v0.3.0 2024-12-10 feature TikTok API structure, dependency mapping Human Coder
v0.3.1 2024-12-12 fix EOF safety rules, 150-char enforcement AI Self-Coder
v1.0.0 2024-12-15 stable Full protocol release, AI training guides Human Coder
v1.1.0 2024-12-18 upgrade Multi-provider support, error recovery AI Self-Coder

---

Appendix A: Quick Reference Card

Commit Message Cheat Sheet

Scenario Command
Add new task only git commit -m "status: new"
Add task + roadmap milestone git commit -m "execute: roadmap vX.X.X"
AI auto-update git commit -m "ai: updated T-00X ✅"
Manual fix git commit -m "fix: corrected T-00X dependencies"
Version bump (Human) git commit -m "release: v1.2.0"

Status Quick Reference

Symbol Meaning Next Action
new Ready for AI Push to trigger
⌛ AI processing Wait 2-5 minutes
✅ Complete Proceed to next task
❌ Failed Check Notes, fix, reset
⚠️ Blocked Manual intervention needed
📅 Scheduled Not yet started

Emergency Commands

```bash
# Full reset (preserve history)
git fetch origin
git reset --hard origin/main

# Force push (use carefully)
git push origin main --force

# Rollback last commit
git reset --soft HEAD~1
git push origin main --force
```

---

End of MAID Protocol Documentation
TikTok-Prompt-Generator · hoopstreet · v1.1.0

For support: hoopstreet143@gmail.com
Repository: https://github.com/hoopstreet/TikTok-Prompt-Generator

```
```
