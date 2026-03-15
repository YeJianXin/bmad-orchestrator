# BMAD Workflow Phases Reference

Complete reference for all 4 BMAD phases, workflows, and project levels.

## Phase 1: Analysis (Optional)

**Purpose:** Understand the problem space, research market/competitors, and define product vision.

**When to use:** Starting new products, major features, or when requirements are unclear.

**When to skip:** Bug fixes, well-defined features, or urgent implementations.

### Phase 1 Workflows

#### Product Brief (`/product-brief`)

**Purpose:** Create comprehensive product vision and high-level requirements.

**Output:** Product brief document with:
- Problem statement
- Target users
- Value proposition
- Key features
- Success metrics
- Constraints

**Duration:** 1-2 hours

**Recommended for:** Level 1+ projects

**Required for:** Level 3+ projects

#### Brainstorm (`/brainstorm`)

**Purpose:** Structured ideation session for features and solutions.

**Output:** Brainstorming session notes with:
- Problem exploration
- Solution ideas
- Feature concepts
- Technical approaches

**Duration:** 30-60 minutes

**Optional for:** All levels

#### Research (`/research`)

**Purpose:** Market analysis, competitive research, technical investigation.

**Output:** Research report with:
- Market analysis
- Competitor comparison
- Technical feasibility
- Recommendations

**Duration:** 2-4 hours

**Optional for:** All levels (recommended for Level 2+)

---

## Phase 2: Planning (Required)

**Purpose:** Define detailed requirements and technical specifications.

**Critical:** Every project must complete at least ONE planning workflow (PRD or Tech Spec).

### Phase 2 Workflows

#### PRD - Product Requirements Document (`/prd`)

**Purpose:** Comprehensive product requirements for multi-feature projects.

**Output:** PRD document with:
- Executive summary
- User stories
- Functional requirements
- Non-functional requirements
- Success criteria
- Acceptance criteria

**Duration:** 2-4 hours

**Required for:** Level 2+ projects

**Recommended for:** Level 1 projects

**Optional for:** Level 0 projects

**When to choose PRD over Tech Spec:**
- Multiple features
- Stakeholder alignment needed
- Product perspective important
- Business requirements complex

#### Tech Spec - Technical Specification (`/tech-spec`)

**Purpose:** Technical design for single features or components.

**Output:** Tech spec document with:
- Technical overview
- Implementation approach
- API contracts
- Data models
- Testing strategy

**Duration:** 1-2 hours

**Required for:** Level 0-1 projects

**Optional for:** Level 2+ projects (supplement to PRD)

**When to choose Tech Spec over PRD:**
- Single feature
- Technical focus
- Limited scope
- Developer-centric work

#### UX Design (`/create-ux-design`)

**Purpose:** Design user interface and user experience.

**Output:** UX design document with:
- User flows
- Wireframes
- UI mockups
- Interaction patterns
- Design system references

**Duration:** 2-6 hours

**Optional for:** Projects with UI components

**Recommended for:** User-facing features

---

## Phase 3: Solutioning (Conditional)

**Purpose:** Design system architecture for medium+ complexity projects.

**Required for:** Level 2+ projects

**Skip for:** Level 0-1 projects (unless significant architectural changes)

### Phase 3 Workflows

#### Architecture (`/architecture`)

**Purpose:** Design system architecture, components, and integrations.

**Output:** Architecture document with:
- System overview
- Component design
- Data flow
- API contracts
- Integration points
- Technology decisions
- Security considerations
- Performance requirements

**Duration:** 2-6 hours

**Required for:** Level 2+ projects

**Optional for:** Level 0-1 with architectural impact

**Content varies by level:**
- Level 2: Component architecture, basic integrations
- Level 3: Comprehensive system design, multiple integrations
- Level 4: Enterprise architecture, platform design, infrastructure

#### Solutioning Gate Check (`/solutioning-gate-check`)

**Purpose:** Validate architecture against requirements before implementation.

**Output:** Gate check report with:
- Requirements coverage
- Risk assessment
- Technical debt analysis
- Readiness score

**Duration:** 30-60 minutes

**Optional for:** Level 2+ projects

**Recommended for:** Level 3+ projects

#### TEA Workflows (Testing & Quality Assurance)

**Purpose:** BMAD TEA (Test Architecture) provides comprehensive testing workflows for quality assurance, test automation, and test governance.

**When to use:** During or after Phase 3 (Solutioning), can run in parallel with Architecture.

**Installation:** TEA framework is installed via `bash scripts/install.sh` (use `--skip-tea` to skip).

**Activation:** Use `/tea-discovery` to explore available TEA workflows.

##### TEA Discovery (`/tea-discovery`)

**Purpose:** Interactive discovery of TEA workflows based on project context.

**Output:** Recommended TEA workflows for your specific project.

**Duration:** 15-30 minutes

**Optional for:** All levels

**When to use:** First time using TEA, or when unsure which TEA workflows to run.

##### Teach Me Testing (TMT) (`/tea-tmt`)

**Purpose:** 7-session fundamental course for learning testing concepts.

**Output:** Testing knowledge and skills through structured learning sessions.

**Duration:** 7 sessions (self-paced)

**Optional for:** All levels

**Recommended for:** Team members new to testing

##### Test Framework (TF) (`/tea-tf`)

**Purpose:** Scaffolding and setup of test framework infrastructure.

**Output:** Configured test framework with CI/CD quality gates.

**Duration:** 4-8 hours

**Required for:** Level 1+ projects

**Optional for:** Level 0 projects

##### Risk-based Test Design (TD) (`/tea-td`)

**Purpose:** Design tests based on risk assessment and priority.

**Output:** Risk-based test plan with prioritized test scenarios.

**Duration:** 2-4 hours

**Required for:** Level 2+ projects

**Optional for:** Level 1 projects

##### CI/CD Quality Gates (CI) (`/tea-ci`)

**Purpose:** Set up automated quality gates in CI/CD pipeline.

**Output:** CI/CD pipeline with automated test execution and quality checks.

**Duration:** 2-4 hours

**Optional for:** All levels

**Recommended for:** Projects with CI/CD



---

## Phase 4: Implementation (Required)

**Purpose:** Execute development through sprints and stories.

**Required for:** All projects (even Level 0 creates at least 1 story)

### Phase 4 Workflows

#### Sprint Planning (`/sprint-planning`)

**Purpose:** Break down requirements into epics and stories, plan sprints.

**Output:**
- Sprint plan with epics and stories
- sprint-status.yaml tracking file
- Story files in docs/stories/

**Duration:** 1-3 hours

**Required for:** Level 1+ projects

**Simplified for:** Level 0 (single story, no sprint)

**Generates:**
- Epics (Level 1+)
- User stories with acceptance criteria
- Story point estimates
- Sprint assignments

#### Create Story (`/create-story`)

**Purpose:** Create individual user story with details.

**Output:** Story file (docs/stories/story-{epic}-{id}.md) with:
- User story format
- Acceptance criteria
- Tasks breakdown
- Estimates
- Dependencies

**Duration:** 15-30 minutes per story

**Required for:** All projects

**Used when:** Adding stories to existing sprint

#### Dev Story (`/dev-story`)

**Purpose:** Implement a specific story with code generation.

**Output:**
- Code implementation
- Tests
- Documentation
- Story marked complete

**Duration:** 30 minutes - several hours

**Required for:** Story implementation

**Process:**
1. Read story file
2. Implement code
3. Write tests
4. Update documentation
5. Mark story complete

#### Code Review (`/code-review`)

**Purpose:** Review implemented code for quality and standards.

**Output:** Review findings and recommendations

**Duration:** 30-60 minutes

**Optional for:** All implementations

**Recommended for:** Level 2+ projects

#### TEA Workflows (Implementation Testing)

**Purpose:** TEA workflows during implementation phase to ensure quality throughout development.

##### ATDD - Acceptance Test-Driven Development (AT) (`/tea-at`)

**Purpose:** Red-phase failing tests for acceptance criteria.

**Output:** Failing acceptance tests that drive implementation.

**Duration:** 1-2 hours per feature

**Required for:** Level 1+ projects

**Optional for:** Level 0 projects

**When to use:** Before implementing each story (ATDD approach)

##### Test Automation (TA) (`/tea-ta`)

**Purpose:** Automate manual tests and create test suites.

**Output:** Automated test suites with execution reports.

**Duration:** 4-12 hours (depends on test coverage)

**Required for:** Level 1+ projects

**Optional for:** Level 0 projects

**When to use:** As features are implemented

##### Test Review (RV) (`/tea-rv`)

**Purpose:** Comprehensive test review with 0-100 scoring.

**Output:** Test review report with quality score and recommendations.

**Duration:** 2-4 hours

**Optional for:** All levels

**Recommended for:** Quality assurance

**When to use:** After implementation complete

##### NFR Assessment (NR) (`/tea-nr`)

**Purpose:** Non-functional requirements testing assessment.

**Output:** NFR test plan covering performance, security, reliability.

**Duration:** 2-6 hours

**Optional for:** All levels

**Recommended for:** Performance-critical projects

**When to use:** After implementation complete

##### Traceability (TR) (`/tea-tr`)

**Purpose:** Requirements to test cases traceability matrix.

**Output:** Traceability matrix linking requirements to tests.

**Duration:** 1-3 hours

**Optional for:** All levels

**Recommended for:** Compliance requirements

**When to use:** After implementation complete

---

## Project Level Decision Matrix

### Level 0: Single Atomic Change (1 story)

| Phase | Workflow | Status |
|-------|----------|--------|
| 1 | Product Brief | Optional |
| 1 | Research | Optional |
| 2 | PRD | Optional |
| 2 | Tech Spec | **Required** |
| 3 | Architecture | Skip |
| 3 | TEA Discovery | Optional |
| 3 | TMT | Optional |
| 3 | TF | Optional |
| 3 | TD | Optional |
| 3 | CI | Optional |
| 4 | Sprint Planning | Simplified (single story) |
| 4 | Dev Story | **Required** |
| 4 | AT | Optional |
| 4 | TA | Optional (minimal) |
| 4 | RV | Optional |
| 4 | NR | Optional |
| 4 | TR | Optional |

**Typical flow:** Tech Spec → Single Story → Implementation

**TEA Integration:** Basic test framework (TF) and minimal automation (TA) if needed

**Example projects:**
- Bug fix
- Configuration change
- Small UI tweak
- Single function addition

---

### Level 1: Small Feature (1-10 stories)

| Phase | Workflow | Status |
|-------|----------|--------|
| 1 | Product Brief | Recommended |
| 1 | Research | Optional |
| 2 | PRD | Recommended |
| 2 | Tech Spec | **Required** |
| 2 | UX Design | Optional |
| 3 | Architecture | Optional |
| 3 | TEA Discovery | Optional |
| 3 | TMT | Optional |
| 3 | TF | **Required** |
| 3 | TD | Optional |
| 3 | CI | Optional |
| 4 | Sprint Planning | **Required** |
| 4 | Create Story | **Required** (multiple) |
| 4 | Dev Story | **Required** |
| 4 | AT | **Required** |
| 4 | TA | **Required** (basic) |
| 4 | RV | Optional |
| 4 | NR | Optional |
| 4 | TR | Optional |

**Typical flow:** Product Brief → Tech Spec → Architecture (optional) → TF → Sprint Planning → AT → Stories → TA → Implementation

**TEA Integration:** Test framework (TF), ATDD (AT), and basic test automation (TA)

**Example projects:**
- New API endpoint
- User profile page
- Data export feature
- Email notifications

---

### Level 2: Medium Feature Set (5-15 stories)

| Phase | Workflow | Status |
|-------|----------|--------|
| 1 | Product Brief | Recommended |
| 1 | Research | Recommended |
| 2 | PRD | **Required** |
| 2 | Tech Spec | Optional |
| 2 | UX Design | Recommended |
| 3 | Architecture | **Required** |
| 3 | Gate Check | Optional |
| 3 | TEA Discovery | Optional |
| 3 | TMT | Optional |
| 3 | TF | **Required** |
| 3 | TD | **Required** |
| 3 | CI | Optional |
| 4 | Sprint Planning | **Required** |
| 4 | Create Story | **Required** (multiple) |
| 4 | Dev Story | **Required** |
| 4 | Code Review | Recommended |
| 4 | AT | **Required** |
| 4 | TA | **Required** |
| 4 | RV | Optional |
| 4 | NR | Optional |
| 4 | TR | Optional |

**Typical flow:** Product Brief → PRD → Architecture → TF → TD → Sprint Planning → AT → Stories → TA → Implementation → Code Review

**TEA Integration:** Full TEA suite including test framework (TF), test design (TD), ATDD (AT), and automation (TA)

**Example projects:**
- User authentication system
- Payment integration
- Dashboard with multiple widgets
- Content management features

---

### Level 3: Complex Integration (12-40 stories)

| Phase | Workflow | Status |
|-------|----------|--------|
| 1 | Product Brief | **Required** |
| 1 | Research | Recommended |
| 2 | PRD | **Required** (detailed) |
| 2 | UX Design | Recommended |
| 3 | Architecture | **Required** (comprehensive) |
| 3 | Gate Check | Recommended |
| 3 | TEA Discovery | Optional |
| 3 | TMT | Optional |
| 3 | TF | **Required** |
| 3 | TD | **Required** |
| 3 | CI | **Required** |
| 4 | Sprint Planning | **Required** (multiple sprints) |
| 4 | Create Story | **Required** (many) |
| 4 | Dev Story | **Required** |
| 4 | Code Review | **Required** |
| 4 | AT | **Required** |
| 4 | TA | **Required** |
| 4 | RV | Optional |
| 4 | NR | Optional |
| 4 | TR | Optional |

**Typical flow:** Product Brief → Research → PRD → Architecture → TF → TD → CI → Gate Check → Multiple Sprints → AT → Stories → TA → Implementation → Code Review

**TEA Integration:** Comprehensive TEA suite including all workflows plus NFR assessment (NR)

**Example projects:**
- Third-party API integration
- Multi-tenant system
- Real-time collaboration features
- Analytics platform

---

### Level 4: Enterprise Expansion (40+ stories)

| Phase | Workflow | Status |
|-------|----------|--------|
| 1 | Product Brief | **Required** (detailed) |
| 1 | Research | **Required** |
| 2 | PRD | **Required** (extensive) |
| 2 | UX Design | **Required** |
| 3 | Architecture | **Required** (system-wide) |
| 3 | Gate Check | **Required** |
| 3 | TEA Discovery | Optional |
| 3 | TMT | Optional |
| 3 | TF | **Required** |
| 3 | TD | **Required** |
| 3 | CI | **Required** |
| 4 | Sprint Planning | **Required** (many sprints) |
| 4 | Create Story | **Required** (extensive) |
| 4 | Dev Story | **Required** |
| 4 | Code Review | **Required** |
| 4 | AT | **Required** |
| 4 | TA | **Required** |
| 4 | RV | Optional |
| 4 | NR | Optional |
| 4 | TR | Optional |
| 4 | TEA Custom | Optional (project-specific) |

**Typical flow:** Product Brief → Research → PRD → UX Design → Architecture → TF → TD → CI → Gate Check → Many Sprints → AT → Stories → TA → Implementation → Code Review → Reviews

**TEA Integration:** Full TEA suite plus custom workflows for enterprise-specific testing needs

**Example projects:**
- Platform migration
- Microservices architecture
- Enterprise SaaS product
- Major system overhaul

---

## Phase Transition Criteria

### Phase 1 → Phase 2

**Can transition when:**
- Product brief completed (if created), OR
- User explicitly skips Phase 1

**Blocking issues:**
- None (Phase 1 is optional)

**Recommendation:** Complete product brief for Level 2+ projects

---

### Phase 2 → Phase 3

**Can transition when:**
- PRD completed (Level 2+), OR
- Tech Spec completed (Level 0-1)

**Blocking issues:**
- No planning document created
- Planning document incomplete or invalid

**Recommendation:** Complete appropriate planning doc before proceeding

---

### Phase 3 → Phase 4

**Can transition when:**
- Architecture completed (Level 2+), OR
- Project is Level 0-1 (skip Phase 3)

**Blocking issues:**
- Level 2+ project without architecture
- Architecture incomplete or not validated

**Recommendation:** Complete architecture for medium+ projects

---

### Phase 4 Complete

**Can transition when:**
- All stories marked "done" in sprint-status.yaml
- Code reviewed (if required)
- Tests passing

**Blocking issues:**
- Incomplete stories
- Failing tests
- Unresolved blockers

**Recommendation:** Complete all stories before closing project

---

## Workflow Dependencies

### Must Complete Before

```
Product Brief → No dependencies (can be first)
Research → No dependencies (can be first)
Brainstorm → No dependencies (can be first)

PRD → Product Brief (recommended, not required)
Tech Spec → Product Brief (recommended, not required)
UX Design → Product Brief or PRD (recommended)

Architecture → PRD or Tech Spec (required)
Gate Check → Architecture (required)

TF (TEA) → PRD or Tech Spec (required)
TD (TEA) → TF (TEA) (recommended)
CI (TEA) → TF (TEA) (required)

Sprint Planning → PRD or Tech Spec (required), Architecture (if Level 2+)
Create Story → Sprint Planning (required)
AT (TEA) → Story created (required)
Dev Story → Story created (required), AT (TEA) (recommended)
TA (TEA) → Dev Story (required)
Code Review → Dev Story (required)
RV (TEA) → TA (TEA) (required)
NR (TEA) → TA (TEA) (required)
TR (TEA) → TA (TEA) (required)
```

### Can Work in Parallel

```
Product Brief + Research
PRD + UX Design (with coordination)
Architecture + TF (TEA) + TD (TEA) + CI (TEA) (Phase 3)
Multiple Dev Stories (different epics)
AT (TEA) + Create Story (Phase 4)
TA (TEA) + Dev Story (Phase 4)
```

### Sequential Requirements

```
Phase 3: Architecture → Gate Check
Phase 3 TEA: TF → TD → CI
Phase 4: Sprint Planning → Create Stories → AT → Dev Stories → TA → Code Review → RV/NR/TR
```

---

## Common Workflow Paths

### Fast Track (Level 0-1)

```
Tech Spec → Sprint Planning → Story → Implementation → Done
```

**Duration:** Hours to days

**Use when:** Small, well-defined changes

---

### Standard Feature (Level 1-2)

```
Product Brief → PRD or Tech Spec → Architecture (if Level 2) →
TF (TEA) → TD (TEA) → Sprint Planning → AT (TEA) → Stories →
TA (TEA) → Implementation → Code Review → Done
```

**Duration:** Days to weeks

**Use when:** Normal feature development

---

### Enterprise Project (Level 3-4)

```
Product Brief → Research → PRD → UX Design → Architecture →
TF (TEA) → TD (TEA) → CI (TEA) → Gate Check → Sprint Planning →
AT (TEA) → Stories → TA (TEA) → Implementation → Code Review →
RV (TEA) → NR (TEA) → TR (TEA) → Iteration → Done
```

**Duration:** Weeks to months

**Use when:** Complex, multi-team projects

---

## Selection Guidance

### When unclear about level, ask:

1. **How many files will change?**
   - 1-3 files: Level 0-1
   - 3-20 files: Level 1-2
   - 20-50 files: Level 2-3
   - 50+ files: Level 3-4

2. **How many stories estimated?**
   - 1 story: Level 0
   - 1-10 stories: Level 1
   - 5-15 stories: Level 2
   - 12-40 stories: Level 3
   - 40+ stories: Level 4

3. **Is architecture design needed?**
   - No: Level 0-1
   - Some: Level 2
   - Significant: Level 3
   - Extensive: Level 4

4. **How long will development take?**
   - Hours-1 day: Level 0
   - 1-5 days: Level 1
   - 1-3 weeks: Level 2
   - 3-8 weeks: Level 3
   - 2+ months: Level 4

### When unclear about workflow, ask:

1. **Is this a new project or existing codebase?**
   - New: Start with Product Brief
   - Existing: Start with Tech Spec or PRD

2. **Do you need stakeholder approval?**
   - Yes: Use PRD
   - No: Use Tech Spec

3. **Is this primarily product or technical?**
   - Product: Use PRD
   - Technical: Use Tech Spec

4. **Do you have clear requirements?**
   - Yes: Skip to Planning
   - No: Start with Analysis

---

## Quick Reference Table

| Project Type | Level | Required Workflows | Duration |
|--------------|-------|-------------------|----------|
| Bug fix | 0 | Tech Spec, Story | Hours |
| Small feature | 1 | Tech Spec, Sprint, Stories | 1-5 days |
| Feature set | 2 | PRD, Architecture, Sprint, Stories | 1-3 weeks |
| Integration | 3 | Brief, PRD, Architecture, Sprints | 3-8 weeks |
| Platform | 4 | Brief, Research, PRD, UX, Architecture, Sprints | 2+ months |
