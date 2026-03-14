---
name: bmad-orchestrator
keyword: bmad
description: Orchestrates BMAD workflows for structured AI-driven development. Routes work across Analysis, Planning, Solutioning, and Implementation phases.
allowed-tools: [Read, Write, Bash, Grep, Glob]
tags: [bmad, orchestrator, workflow, planning, implementation]
platforms: [Claude, Gemini, Codex, OpenCode]
version: 1.0.0
source: user-installed skill
---

# bmad-orchestrator - BMAD Workflow Orchestration

## When to use this skill

- Initializing BMAD in a new project
- Checking and resuming BMAD workflow status
- Routing work across Analysis, Planning, Solutioning, and Implementation
- Managing structured handoff between phases

---

## Installation

```bash
npx skills add https://github.com/supercent-io/skills-template --skill bmad-orchestrator
```

## Codex 사용 참고

`bmad-orchestrator`의 기본 실행 경로는 Claude Code입니다.  
Codex에서 직접 동일한 흐름으로 사용하려면 `omx`/`ohmg` 등 상위 오케스트레이션 경로를 통해 BMAD 단계를 운영하는 것을 권장합니다.

---

## BMAD Execution Commands

## 플랫폼별 적용 상태 (현재 지원 기준)

| 플랫폼 | 현재 지원 방식 | 적용 조건 |
|---|---|---|
| Gemini CLI | 네이티브(권장) | `bmad` 키워드 등록 후 `/workflow-init` 실행 |
| Claude Code | 네이티브(권장) | 스킬 설치 + `기억해` 패턴 |
| OpenCode | 오케스트레이션 연동 | `omx`/`ohmg`/`omx` 류 브릿지 사용 |
| Codex | 오케스트레이션 연동 | `omx`/`ohmg`류 브릿지 사용 |

`현재 스킬만`으로 가능한지:  
- Gemini CLI/Claude Code: **가능**  
- OpenCode/Codex: **가능(오케스트레이션 경유)**

Use these in your AI session:

```text
/workflow-init
/workflow-status
```

Typical flow:

1. Run `/workflow-init` to bootstrap BMAD config.
2. Move through phases in order: Analysis -> Planning -> Solutioning -> Implementation.
3. Run `/workflow-status` any time to inspect current phase and progress.

---

## Quick Reference

| Action | Command |
|--------|---------|
| Initialize BMAD | `/workflow-init` |
| Check BMAD status | `/workflow-status` |


---

## plannotator Integration (Phase Review Gate)

Each BMAD phase produces a key document (PRD, Tech Spec, Architecture). Before transitioning to the next phase, review that document with **plannotator** and auto-save it to Obsidian.

### Why use plannotator with BMAD?

- **Quality gate**: Approve or request changes before locking in a phase deliverable
- **Obsidian archive**: Every approved phase document auto-saves with YAML frontmatter and `[[BMAD Plans]]` backlink
- **Team visibility**: Share a plannotator link so stakeholders can annotate the PRD/Architecture before implementation begins

### Phase Review Pattern

After completing any phase document, submit it for review:

```bash
# After /prd → docs/prd-myapp-2026-02-22.md is created
bash scripts/phase-gate-review.sh docs/prd-myapp-2026-02-22.md "PRD Review: myapp"

# After /architecture → docs/architecture-myapp-2026-02-22.md is created
bash scripts/phase-gate-review.sh docs/architecture-myapp-2026-02-22.md "Architecture Review: myapp"
```

Or submit the plan directly from within your AI session:

```text
# In Claude Code after /prd completes:
planno — review the PRD before we proceed to Phase 3
```

The agent will call `submit_plan` with the document content, opening the plannotator UI for review.

### Phase Gate Flow

```
/prd completes → docs/prd-myapp.md created
       ↓
 bash scripts/phase-gate-review.sh docs/prd-myapp.md
       ↓
 plannotator UI opens in browser
       ↓
  [Approve]              [Request Changes]
       ↓                        ↓
 Obsidian saved          Agent revises doc
 bmm-workflow-status     Re-submit for review
 updated automatically
       ↓
 /architecture (Phase 3)
```

### Obsidian Save Format

Approved phase documents are saved to your Obsidian vault with:

```yaml
---
created: 2026-02-22T22:45:30.000Z
source: plannotator
tags: [bmad, phase-2, prd, myapp]
---

[[BMAD Plans]]

# PRD: myapp
...
```

### Quick Reference

| Phase | Document | Gate Command |
|-------|----------|--------------|
| Phase 1 → 2 | Product Brief | `bash scripts/phase-gate-review.sh docs/product-brief-*.md` |
| Phase 2 → 3 | PRD / Tech Spec | `bash scripts/phase-gate-review.sh docs/prd-*.md` |
| Phase 3 → 4 | Architecture | `bash scripts/phase-gate-review.sh docs/architecture-*.md` |
| Phase 4 done | Sprint Plan | `bash scripts/phase-gate-review.sh docs/sprint-status.yaml` |

---

## BMAD TEA Framework Integration

BMAD TEA (Test Architecture) provides comprehensive testing workflows for quality assurance, test automation, and test governance. TEA is a **standalone workflow** that can be triggered anytime after Phase 3 (Solutioning).

### Installation

TEA framework is installed automatically when running the BMAD setup:

```bash
bash scripts/install.sh
```

To skip TEA installation:
```bash
bash scripts/install.sh --skip-tea
```

### When to Use TEA

- **After Phase 3 (Solutioning)**: Set up test framework and design tests
- **During Phase 4 (Implementation)**: Apply ATDD and automate tests
- **After Phase 4 (Complete)**: Review tests, assess NFRs, verify traceability
- **Anytime**: Learn testing fundamentals or explore workflows

### TEA Workflow Commands

| Category | Command | Purpose |
|----------|---------|---------|
| **Education** | `/tea-discovery` | Discover TEA workflows for your project |
| **Education** | `/tea-tmt` | Teach Me Testing - 7-session course |
| **Strategy** | `/tea-td` | Risk-based Test Design |
| **Foundation** | `/tea-tf` | Test Framework setup |
| **Foundation** | `/tea-ci` | CI/CD Quality Gates |
| **Implementation** | `/tea-at` | ATDD (red-phase failing tests) |
| **Implementation** | `/tea-ta` | Test Automation |
| **Audit** | `/tea-rv` | Test Review (0-100 score) |
| **Audit** | `/tea-nr` | NFR Assessment |
| **Audit** | `/tea-tr` | Traceability |

### TEA by Project Level

| Level | Required TEA Workflows |
|-------|------------------------|
| Level 0 | TF (optional), TA (minimal) |
| Level 1 | TF, AT, TA (basic) |
| Level 2 | TF, TD, AT, TA, RV, TR |
| Level 3 | All TEA workflows + NR |
| Level 4 | All TEA workflows + Custom |

### Typical TEA Integration Flow

```
Phase 3 Complete (Architecture)
       ↓
/tea-tf → Set up test framework
/tea-td → Risk-based test design
/tea-ci → Configure CI/CD quality gates
       ↓
Phase 4 (Implementation)
       ↓
/tea-at → ATDD for each story (red-phase tests)
/tea-ta → Automate tests as features complete
       ↓
Phase 4 Complete
       ↓
/tea-rv → Comprehensive test review
/tea-nr → NFR assessment
/tea-tr → Traceability verification
```

### Getting Started with TEA

1. **Discover TEA workflows:**
   ```text
   /tea-discovery
   ```

2. **Learn testing fundamentals (optional):**
   ```text
   /tea-tmt
   ```

3. **Set up test framework (after Phase 3):**
   ```text
   /tea-tf
   ```

4. **Apply ATDD during implementation:**
   ```text
   /tea-at
   ```

### TEA Workflow Details

#### `/tea-discovery`
Interactive discovery of TEA workflows based on your project context. Use this first to understand which TEA workflows are recommended for your project.

#### `/tea-tmt` (Teach Me Testing)
7-session fundamental course covering testing concepts, strategies, and best practices. Recommended for team members new to testing.

#### `/tea-td` (Test Design)
Risk-based test design that prioritizes test scenarios based on risk assessment. Creates a comprehensive test plan with prioritized test cases.

#### `/tea-tf` (Test Framework)
Scaffolds and sets up test framework infrastructure including test runners, mocking, fixtures, and CI/CD integration.

#### `/tea-ci` (CI/CD Quality Gates)
Configures automated quality gates in your CI/CD pipeline, ensuring tests run automatically and quality standards are met.

#### `/tea-at` (ATDD)
Acceptance Test-Driven Development workflow that creates red-phase failing tests for acceptance criteria before implementation.

#### `/tea-ta` (Test Automation)
Automates manual tests and creates comprehensive test suites with execution reports and coverage metrics.

#### `/tea-rv` (Test Review)
Comprehensive test review with 0-100 scoring, providing quality assessment and actionable recommendations.

#### `/tea-nr` (NFR Assessment)
Non-functional requirements testing assessment covering performance, security, reliability, scalability, and other quality attributes.

#### `/tea-tr` (Traceability)
Creates a traceability matrix linking requirements to test cases, ensuring full coverage and compliance.

### TEA + plannotator Integration

TEA workflows can also be reviewed with plannotator for quality assurance:

```bash
# After test design
bash scripts/phase-gate-review.sh docs/tea-test-design-*.md

# After test review
bash scripts/phase-gate-review.sh docs/tea-test-review-*.md
```

This ensures test artifacts undergo the same rigorous review process as other BMAD deliverables.