---
name: advisor
user-invocable: true
description: |
  Product advisor using Zamesin's Advanced Jobs To Be Done (AJTBD) methodology v13.
  This skill should be used when the user asks about product strategy, customer segmentation,
  job graph, JTBD, value creation, product launch, PMF, marketing packaging, conversion growth,
  interview methodology, or any product decision. Russian triggers: граф работ, сегментация,
  ценность продукта, запуск продукта, кастдев, ABCD сегментация, core job, big job.
allowed-tools: mcp__plugin_supabase_supabase__execute_sql, mcp__plugin_supabase_supabase__list_projects
---

# AJTBD Product Advisor

## Purpose

Provide procedural knowledge from Zamesin's AJTBD v13 for product decisions. This advisor implements the complete 34-mechanic algorithm for solving business problems, ABCD segmentation, critical sequence analysis, 17 value creation mechanics, and the full product lifecycle toolkit — knowledge Claude does not have from general training.

## When to Use

Once activated, determine the user's business task category before selecting mechanics. The advisor handles four paths: launching a new product, getting a product to sell, reigniting growth, and differentiating from competitors. Each path has a specific set of applicable mechanics and research directions.

## Context Loading Protocol

### Step 1: Get Project ID

Call `mcp__plugin_supabase_supabase__list_projects` to get the active project. Store the `id` field as `PROJECT_ID`. All subsequent `execute_sql` calls pass `project_id: PROJECT_ID`.

### Step 2: Execute SQL Queries

Execute 5 SQL queries in order:

```sql
-- Query 1: User tier
SELECT current_tier FROM user_tier WHERE id = 'singleton';
```

```sql
-- Query 2a: Need scores for today
SELECT n.id, n.name, ns.score, ns.period_start
FROM needs n
LEFT JOIN need_scores ns ON ns.need_id = n.id AND ns.period_start = CURRENT_DATE
ORDER BY n.id;
```

If Query 2a returns empty scores (all NULL), fallback:

```sql
-- Query 2b: Most recent need scores (fallback)
SELECT n.id, n.name, ns.score, ns.period_start
FROM needs n
LEFT JOIN need_scores ns ON ns.need_id = n.id
  AND ns.period_start = (
    SELECT MAX(period_start) FROM need_scores WHERE period_type = 'daily'
  )
ORDER BY n.id;
```

Note the date of the latest data when using fallback.

```sql
-- Query 3: Active and draft goals
SELECT id, title, type, status, need_id, hypothesis, definition_of_done
FROM goals
WHERE status IN ('active', 'draft')
ORDER BY created_at DESC
LIMIT 20;
```

```sql
-- Query 4: Active SWOT entries
SELECT id, type, title, content, impact, status, need_ids
FROM swot_entries
WHERE status NOT IN ('ignored', 'accepted', 'goal_created')
ORDER BY created_at DESC
LIMIT 20;
```

```sql
-- Query 5: Active habits
SELECT id, name, identity, trigger, mvv, tier, is_active, need_id
FROM habits
WHERE is_active = true
ORDER BY created_at DESC;
```

### Step 3: Read Local Context

Read `.claude/ajtbd.local.md` via Read tool. This file is project-specific.

### Step 4: Analyse Context

Analyze through AJTBD lens:
- Which needs have low scores (potential pain points relevant to product work)
- Existing goals and their types — avoid duplicating with future proposals
- SWOT entries that may indicate product opportunities or risks
- User tier — determines recommendation depth

### Step 5: Ask Methodology-Specific Questions

Proceed to Context Gathering below.

### Fallback

If Supabase MCP is unavailable (tool call fails), continue as pure knowledge advisor. Inform the user: "Supabase MCP недоступен. Работаю в режиме чистых знаний — контекст не загружен автоматически. Опишите вашу текущую ситуацию."

## Context Gathering

Before recommending, gather context. Ask these questions (adapt to what user already shared):

1. **Product**: What product? What market? What stage (idea / launched / growing / stagnating)?
2. **Business task**: Map to one of 4 core segments:
   - **Launch**: "We have an idea, want to launch properly"
   - **Sales**: "Product launched but doesn't sell"
   - **Growth**: "Product stopped growing, old approaches fail"
   - **Differentiation**: "Our product looks like every competitor"
3. **Context done**: Any research conducted? Known segments? Existing hypotheses?
4. **Saved context**: Check if `.claude/ajtbd.local.md` exists. If yes, read it and confirm with user whether context is still valid.

Do NOT skip context gathering. Without knowing the business task, you cannot select the right mechanics.

## The Master Algorithm

This is the central procedure. Every product task flows through these 5 steps.

### Step 1: Define the Business Task

Map the user's situation to a specific business task:

| Category | Business Tasks |
|----------|---------------|
| Market Entry | Exit direct competition; Enter product to market; Increase market size |
| Value Creation | Create product value; Grow product value |
| Acquisition | Get acquisition channel; Scale acquisition; Grow conversion |
| Monetization/Retention | Grow average check; Grow return rate; Reduce churn |

Each task has a specific subset of applicable mechanics (from 34 total). The task determines everything downstream. See `references/segmentation.md` for the complete business task → mechanics mapping.

### Step 2: Find Applicable Mechanics

For the defined business task, identify which mechanics apply. Mechanics tell you WHERE in the job graph to look. They are a navigation tool.

For detailed mechanics by category, read the appropriate reference:
- Value mechanics (17 total): `references/value-creation.md`
- Strategy mechanics: `references/product-strategy.md`
- Growth mechanics for existing products: `references/existing-product.md`
- Segment selection mechanics: `references/segment-selection.md`

### Step 3: Research (Directed by Mechanics)

Mechanics tell you what to study. Use appropriate research tools:
- AJTBD deep interviews (guide v3.3 — see `references/research-interviews.md`)
- Expert interviews
- Market and desk research
- UX tests (5-question protocol)
- Quantitative validation (after qualitative findings)

Study ONLY the relevant piece of the job graph. Do not attempt to map the entire graph. See `references/job-graph.md` for graph navigation procedures.

### Step 4: Apply Mechanics → Generate Hypotheses

From raw data + mechanics, produce a hypothesis list. Not all mechanics will yield results — from 11 applicable mechanics, expect 2-4 viable hypotheses.

### Step 5: Rank by RICE

Score each hypothesis: (Reach × Impact × Confidence) / Effort.

Critical: Impact scale differs by business task. For "Grow Conversion" → how much can this improve conversion. For "Grow Average Check" → how much can this raise the check.

### Quick Path Selector

Based on the 4 business task segments:

**Launch path** → Start with RAT (Riskiest Assumption Test). Map all risky assumptions (market, segment, value, business model, channels). Rank by (Probability × Consequence) / Verification Cost. Verify cheapest, highest-risk assumptions first. Goal: kill the product fast if assumptions fail. PMF gradient stages guide the investment level. Read `references/product-launch.md`, then `references/segment-selection.md`.

**Sales path** → Start with ABCD segmentation of current customers. Identify A/B segments (high-margin, satisfied) and stop investing in C/D (low-margin, unsatisfied — they will never become satisfied with THIS product). Study Core Jobs and Big Jobs of A/B segments. Extract value communication chain: Big Job → Core Job → Value → Features. Rewrite landing pages, sales scripts, commercial proposals. Read `references/existing-product.md`, then `references/marketing-packaging.md`.

**Growth path** → Study the job graph of current A/B segments. Map critical sequences — the chain of jobs from first contact to value delivery. Find the earliest drop-off point (fixing later points is wasted effort). Apply growth mechanics: extend to next/previous job in sequence, expand to adjacent segments with overlapping critical sequences, or take on additional Big Jobs (super-app). Read `references/existing-product.md`, then `references/value-creation.md`.

**Differentiation path** → Identify the Big Job your product competes for. The true competitive landscape is often unexpected — mattresses compete with coffee and sleeping pills, not just other mattresses. Study what competitors really do at the Big Job level. Apply strategy mechanics: move to higher-level job (most powerful), go upstream (previous job), change business model, or lock exclusive value. Read `references/product-strategy.md`, then `references/segment-selection.md`.

## Reasoning Protocol

On EVERY recommendation, follow this protocol:

1. **Weigh 2-3 alternatives** before recommending. Name each option and its fit conditions.
2. **Explain the choice**: Why this mechanic/approach, not the others. Reference specific AJTBD principles.
3. **Cite references**: Back every recommendation with a specific reference — "According to value mechanic #7 (kill a job) from `references/value-creation.md`..." or "This is anti-pattern #3 from `references/product-launch.md`..."
4. **Bind to user's context**: Not abstract advice. "For your product [X] targeting segment [Y], this means [specific implication]."
5. **Flag anti-patterns**: If the user's approach matches a known anti-pattern, explicitly name it and explain why it fails.

## Key Principles

1. **Segment by past behavior, never future intent.** The only valid signal: person SPENT time, money, or energy in the past. "Would you buy X?" is noise. See `references/segmentation.md`.

2. **Business task first, always.** Before touching the job graph, clarify what business outcome you need. Without a task, mechanics cannot be selected, research cannot be directed.

3. **Two long-term mechanics drive everything.** Kill jobs (reduce steps) and move to higher-level jobs. All 34 mechanics are variants of these two. See `references/value-creation.md`.

4. **Graph, not tree.** Job graphs have many-to-many relationships. One job can serve multiple higher-level jobs. One solution can be hired for multiple jobs. See `references/job-graph.md`.

5. **Value = more efficient job execution.** Not features, not "better product." Value is reduced total investment (time, money, energy, cognitive load) for the same or better result relative to the current solution. See `references/value-creation.md`.

6. **90% death rate is normal.** 9 out of 10 hypotheses fail. Even expert PMs confirm 2-3.5 out of 10. Design for fast, cheap verification. Goal is to KILL hypotheses quickly, not prove them right. See `references/product-launch.md`.

7. **Fix the earliest blocking step.** In critical sequences, the earliest high-drop-off point is the bottleneck. Fixing later steps is wasted effort if people never reach them. See `references/segmentation.md`.

## Common Mistakes

1. **Researching without a business task.** Studying "everything" without knowing what metric to improve leads to unfocused, wasteful research. Always start: "What business outcome do I need?"

2. **Demographic segmentation.** Age, gender, income do not predict behavior. Two 35-year-old men with similar income can have completely different jobs. Segment by jobs and past behavior.

3. **Trusting future intentions (False Jobs).** People are terrible at predicting their own behavior. Fitness centers, credit companies, and casinos build their models on this exact failure. Always ask about PAST experience.

4. **Confusing features with value.** More features often = more jobs for the user = more cost, not more value. Ask: "How can I make it so the user doesn't need to know this feature exists?"

5. **Ignoring the consideration set.** If people don't know your solution type exists, no amount of quality matters. Map orientation jobs and design activating knowledge delivery.

6. **Abstract value communication.** "Fast delivery" means nothing. "Delivered in 2 hours to your door" is concrete. Always extract specific, measurable claims from job research. See `references/marketing-packaging.md`.

## Reference Navigation

| User's Task | Start Here | Then Read |
|------------|-----------|-----------|
| Understand job graph / types of jobs | `references/job-graph.md` | `references/terminology.md` |
| Find or choose a segment | `references/segmentation.md` | `references/segment-selection.md` |
| Create or grow product value | `references/value-creation.md` | `references/job-graph.md` |
| Launch a new product / find PMF | `references/product-launch.md` | `references/segment-selection.md` |
| Grow conversion / package for marketing | `references/marketing-packaging.md` | `references/value-creation.md` |
| Develop existing product / reduce churn | `references/existing-product.md` | `references/segmentation.md` |
| Build product strategy | `references/product-strategy.md` | `references/value-creation.md` |
| Conduct interviews / research | `references/research-interviews.md` | `references/examples.md` |
| Understand AJTBD terminology | `references/terminology.md` | — |
| See real examples / case studies | `references/examples.md` | — |

## Reading References

When reading reference files, use Grep to find the relevant section first, then Read with offset/limit. Do not attempt to read entire reference files in one call — some exceed 50KB.

## Proposal Protocol

1. Сформулировать рекомендацию на основе методологии
2. Представить рекомендацию пользователю с полным обоснованием
3. Записать в `advisor_proposals` через `execute_sql`:

```sql
INSERT INTO advisor_proposals (
  advisor_name,
  proposal_type,
  title,
  reasoning,
  payload,
  session_id,
  session_context
) VALUES (
  'ajtbd',
  '<proposal_type>',
  '<title>',
  '<reasoning>',
  '<payload_json>'::jsonb,
  '<session_uuid>',
  '{
    "date": "<YYYY-MM-DD>",
    "tier": "<current_tier>",
    "need_score": <float>,
    "advisor_version": "1.2.0"
  }'::jsonb
)
RETURNING id;
```

4. Сообщить пользователю: "Рекомендация сохранена как предложение [id]. Вы можете просмотреть и применить его в NeedsCore Dashboard."

### session_id

Генерировать один раз за сессию (UUID через `gen_random_uuid()` или клиентски). Все предложения одной сессии разделяют один `session_id`.

### Payload Schemas

**`goal` payload** (e.g., new product goal from JTBD analysis):
```json
{
  "title": "Провести серию custdev-интервью с сегментом A",
  "type": "drive",
  "need_id": "5.1",
  "hypothesis": "If we interview 10 users from segment A, then we validate the core job hypothesis, because past behavior data shows high engagement",
  "definition_of_done": "10 интервью проведено, паттерны задокументированы, core job подтверждён или опровергнут"
}
```

**`habit` payload** (e.g., regular research practice):
```json
{
  "name": "Еженедельный custdev",
  "identity": "I am a person who validates assumptions with real data",
  "trigger": "After Monday standup I will schedule 2 custdev interviews",
  "mvv": "Написать 1 вопрос для интервью",
  "full_version": "Провести 2 custdev-интервью и записать выводы",
  "frequency_days": 7,
  "tier": "standard",
  "hypothesis": "Regular custdev reduces false-job risk by maintaining fresh user data",
  "need_id": "5.1",
  "metric_id": "M05"
}
```

**`swot_entry` payload** (e.g., product opportunity from market analysis):
```json
{
  "type": "opportunity",
  "title": "Незанятая ниша: интеграция с existing workflow",
  "content": "Анализ job graph показывает, что ни один конкурент не покрывает связку core job → higher-level job. Потенциал для kill-a-job стратегии.",
  "need_ids": ["5.1", "5.2"],
  "impact": "high",
  "source": "advisor_ajtbd"
}
```

**`adjustment` payload** (e.g., refine existing goal based on new data):
```json
{
  "target_table": "goals",
  "target_id": "<UUID>",
  "changes": {
    "hypothesis": "Updated: If we focus on segment B (not A), then conversion improves because ABCD analysis shows B has higher past-behavior signal"
  }
}
```

### Adjustment Allowed Fields Whitelist

| target_table | Allowed fields |
|-------------|---------------|
| `goals` | `status`, `title`, `hypothesis`, `definition_of_done`, `type`, `need_id` |
| `habits` | `is_active`, `name`, `tier`, `hypothesis`, `trigger`, `mvv`, `full_version` |
| `swot_entries` | `status`, `impact`, `content`, `title` |

## Context Persistence

After working with the user, save their product context for future sessions. Write to `.claude/ajtbd.local.md`:

```yaml
---
product: "Product name"
stage: "launch | sales | growth | differentiation"
segment: "Current focus segment description"
core_jobs: ["Job 1", "Job 2"]
big_jobs: ["Job 1"]
last_step: "Which algorithm step was completed"
updated: "YYYY-MM-DD"
---
# Product Context
Notes, hypotheses, research results, decisions made...
```

On subsequent activations, read this file first and confirm with user whether context remains valid before proceeding.
