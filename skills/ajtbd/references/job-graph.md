# Job Graph: Construction, Types, Properties, and Analysis (Zamesin v13)

## Metadata
- **Source**: Course "Kak delat produkt" (How to build product), Modules 01_07, 01_08, 01_01
- **Author**: Ivan Zamesin
- **Version**: v13
- **Type**: course lectures + interview guides
- **Scope**: How to build, read, and use job graphs for product decisions

---

## What is a Job Graph

A job graph is a hierarchical structure of jobs showing relationships between higher-level and lower-level jobs. It is the second critical unit of analysis in AJTBD (alongside individual jobs).

Key properties:
- It is a mathematical GRAPH (not a tree) because it has many-to-many relationships
- One lower-level job can serve MULTIPLE higher-level jobs
- One solution can be hired for MULTIPLE jobs (by the same person or different people)
- A single person's graph can contain hundreds of jobs
- Across a market segment, the graph can contain thousands of jobs
- You NEVER need to know the entire graph -- only pieces relevant to your business task

## How the Graph is Formed

The graph is determined by TWO choices:

### Choice 1: Product creators propose a graph
Product makers decide what jobs a person must execute to accomplish their higher-level job using the product. Every design decision (features, steps, channels, interfaces) shapes the proposed job graph.

Example: An online course creator decides: course is in Zoom, has a personal dashboard, Telegram chats, slides, recorded lectures, interview guides, practice sessions, Q&A sessions. This set of decisions defines the graph of jobs every participant must traverse.

### Choice 2: The customer agrees (or not)
The customer evaluates the proposed graph and either accepts it or rejects it for a competing solution. The customer compares: how much time, money, energy the graph requires vs. the benefit received.

Example: Customer sees the course requires 10 hours/week for a month and thinks "Too complex. I'll hire a consultant instead." The customer rejected the proposed graph.

**Both choices together** determine which graph the person actually traverses, their experience, satisfaction, and future solution evaluation.

## Seven Principles of Graph Formation

### Principle 1: You don't need the full graph for every task
Not all business tasks require a job graph, and you never need the entire graph. Focus on the pieces relevant to your specific business task.

**When job graph IS needed:**
- Creating product value
- Retaining customers
- Growing return rate
- Growing conversion
- Understanding competitive landscape

**When job graph is LESS needed:**
- Segment search (unless strong competition, expensive acquisition channels, or you need viral mechanics)

**For each business task, you need different pieces of the graph.** Example: for a real estate developer growing conversion, you need the purchase decision sequence. You don't need the full life graph of every buyer.

### Principle 2: Solution for higher-level job = sum of solutions for all lower-level jobs
The "solution" a person hires for a high-level job is actually the aggregate of ALL solutions hired for every lower-level job in the graph.

Example: "Vacation at the seaside" solution is not just "I organize everything myself" -- it's "I use Aviasales + I book on Booking.com + I stay at Hotel X + I eat at Cafe Y + I visit Beach Club Z." All lower-level solutions combine into one composite solution for the higher-level job.

**Implication**: Improving ANY lower-level solution improves the composite higher-level solution. Degrading any lower-level solution degrades the whole.

### Principle 3: One lower-level job can serve multiple higher-level jobs
This is the key graph property (many-to-many). When a lower-level job serves more higher-level jobs, the person's motivation to execute it INCREASES.

Example: "Learn AJTBD methodology" serves both "grow in career" and "validate my pet project idea." Both higher-level jobs become stronger motivators. Communicate ALL higher-level jobs that a lower-level job serves to maximize motivation.

### Principle 4: One solution can be hired for multiple jobs (same person or different people)
This is fundamental for scaling and retention strategies.

**Same person, multiple jobs**: Example: Yandex Taxi user takes Economy to the metro (cheap/fast job), Comfort to meetings (comfort/safety job), Business for calls during rides (quiet/professional job). This drives return rate, LTV growth, average check growth.

**Different people, same jobs**: Different people hiring the same solution for the same type of job = market scaling opportunity. One segment hires Economy, another hires Business.

### Principle 5: People predict the job graph and compare predictions vs. actual results
The brain automatically and unconsciously predicts what the job graph will look like with a given solution, then compares the prediction to actual experience. This comparison drives satisfaction/dissatisfaction and is the territory of value creation.

### Principle 6: People can refuse to execute jobs
Non-execution can signal either: the job is not important enough (low motivation) or it's too difficult (barriers). Distinguish between these:
- If not important enough: for research/segmentation, select people who DID execute the job in the past
- If motivated person drops off: signal of a PROBLEM in the critical sequence that needs fixing

### Principle 7: Knowledge and experience activate execution of specific jobs with specific solutions
What a person knows determines which solutions they consider and which graph they traverse. New knowledge can rewrite the entire sub-graph.

## Types and Properties of Jobs

### Sequential Jobs
**Definition**: Jobs that form a step-by-step progression toward the higher-level job result. The result of one job unlocks the next.

**Key property**: Value/benefit is received at or near the END of the sequence. Until the person completes the full sequence, they do NOT get the higher-level job's result.

**Implication for product design**: Kill preceding jobs to get the person to the value-delivering step faster. Fewer lower-level jobs = less total investment = higher perceived value.

**How to research**: Ask "Walk me through the steps -- what did you do to [accomplish the higher-level job]?" List all actions, group them into job descriptions.

### Frequency Jobs
**Definition**: Jobs executed with regular periodicity (daily, weekly, monthly, yearly).

**Key property**: The same job can be BOTH sequential (part of a sequence) AND frequency-based. Example: in weekly grocery ordering, "select items" and "pay for cart" are sequential within one order but happen 3x/week, 100x/year.

**Implication for business model**: Products built on recurring use need segments whose jobs are executed MORE FREQUENTLY. Frequency directly impacts cohort retention and LTV.

**How to research**: Ask "What are your typical usage scenarios?" or "How often do you do [this]?"

### Alternating Pattern in Graphs
When studying job graphs, you will frequently see alternation: sequential -> frequency -> sequential -> frequency at different levels. Recognize this pattern to ask the right interview questions at each level.

### Viral Jobs
**Definition**: Jobs done FOR or WITH another person, where the second person may start using the product as a result.

**Criteria for evaluating virality**:
1. Does the first person's job execution expose the second person to the product?
2. Can the second person start executing their OWN jobs with the product independently?
3. How frequently does this viral job occur?

**Strategic use**: Build entire products around viral jobs (Figma, Miro, Google Docs). When entering a market, prioritize segments with more viral jobs executed more frequently.

### Tax Jobs
**Definition**: Unplanned jobs arising because a hired solution failed to execute (or poorly executed) a job.

**Emotional signature**: Person experiences irritation, anger -- they predicted the solution would work, were wrong, and must now spend additional effort.

**Strategic use**: Tax jobs of competing solutions are OPPORTUNITIES. Find what tax jobs competitors create, then build a solution that eliminates them.

**How to identify**: In interviews, listen for complaints, workarounds, "I had to do X myself because Y didn't work."

### Orientation Jobs
**Definition**: Jobs that update the person's consideration set and knowledge about available solutions.

**Identifying verbs**: understand, learn, find, choose, figure out, decide, compare.

**Position in graph**: Almost always among the FIRST low-level sequential jobs. The result of an orientation job (choosing a solution) determines the ENTIRE subsequent sub-graph.

**Mechanism**: Person discovers options -> evaluates costs/benefits/graphs for each -> selects solution -> selected solution "jumps" into the higher-level job -> defines the rest of the graph.

**Example**: Person moving to new city -> orientation job "understand where I'll live" -> discovers options (rent, friends, hotel) -> evaluates each -> chooses "rent apartment" -> this determines subsequent jobs (find apartment, sign lease, move in...).

### False Jobs
**Definition**: Fantasies about the future. Everything a person says they PLAN to do.

**Detection rule**: Person speaks in future tense about intended actions.

**Counter-measure**: Always ask "Have you done anything in the PAST to achieve this?" If no past action exists, classify as false job and do not build strategy on it.

**Segmentation rule**: Only segment by PAST BEHAVIOR -- person spent time, money, or energy. This is confirmed by experience in 95-98%+ of cases.

### Sleeping Jobs
**Definition**: Jobs that don't exist yet but will appear when the person receives activating knowledge about a dramatically better solution.

**Activation mechanism**: When a person learns that a 10x better way to accomplish their higher-level job exists, the entire sub-graph of new lower-level jobs "wakes up."

**Connection to Crossing the Chasm**: Zamesin considers Geoffrey Moore's "Crossing the Chasm" to be fundamentally about loading activating knowledge about an unfamiliar solution type to people with different openness levels to new things.

## Job Hierarchy

### Core Job (Root Job)
- Highest level in the relevant graph portion
- Does not change for decades/centuries/millennia ("have a safe home", "be healthy")
- Contains NO product-specific details
- Closest to fundamental psychological needs
- Strongest emotional responses when threatened or fulfilled

### Big Job
- The high-level job your product and competitors actually compete for
- Lower than Core Job, higher than product-specific jobs
- Used as the anchor for activating knowledge
- Defines your TRUE competitive landscape (often unexpected competitors)
- Example: mattresses compete not with other mattresses but with coffee, sleeping pills, quitting the job -- all for Big Job "continue functioning when sleep-deprived"

### Sub Jobs (Lower-level Jobs)
- Progressively more product-specific as you go lower
- Change faster over time (higher-level jobs are stable for decades, lower-level jobs change frequently)
- Eventually disappear as products simplify the graph

### Vertical Properties
- **Higher = more emotional**: Emotions intensify as you move up the graph (closer to needs)
- **Higher = less product-specific**: Job descriptions contain fewer product details
- **Higher = more stable**: High-level jobs don't change for decades; low-level jobs change frequently
- **Lower = more product-specific**: Job descriptions increasingly reference specific product features
- **Lower = more volatile**: These jobs appear and disappear as solutions evolve

## How to Study a Job Graph

### Starting Point: Any Action
Start from ANY single action/fact ("I did X") and dig in both directions.

### Digging UP (to higher-level jobs)
Ask: "What result did you want from [action]?" -> You get the job.
Then: "Why did you do that? So that what?" -> You get higher-level job(s).
Continue until you reach a stable, product-independent core job.

### Digging DOWN (to lower-level jobs)
For SEQUENTIAL lower-level jobs: "Walk me through the steps -- what did you do to [accomplish the job]?"
For FREQUENCY lower-level jobs: "What are your typical usage scenarios? Who does what?"

### Digging BACKWARD (previous versions)
Ask: "What did you do BEFORE [this action] to [accomplish the higher-level job]?"
Reveals the chain of solution switches and consideration set evolution.

### Digging FORWARD (next versions)
Ask: "What did you do AFTER [this action] to [accomplish the higher-level job]?"
Reveals whether the person continued, switched solutions, or dropped off.

### Interview Navigation Block (New in v3.3)
Purpose: In the first few minutes of an interview, quickly map out which jobs are being hired for, BEFORE deep-diving.

Two starting points:
1. **Starting from solution hypothesis**: "In what situation were you when you decided to [use solution X]?" + "What results did you expect?"
2. **Starting from job hypothesis**: "Tell me, how do you [accomplish job X]?" + "In what situations are you usually when you [do this]?" + "What results do you expect?"

Output: Short list of jobs with contexts (when) and expected results (want/so-that). Takes ~10 minutes. Then select 2-3 most important/problematic to deep-dive.

### Selection Criteria for Deep-Dive
Depends on business task:
- **Growing return rate**: "Which of these is most problematic AND you do most often?"
- **Communicating value to new customers**: "Which of these is most important AND you're most satisfied with using our solution?"
- **Finding segments**: "Which of these was most important and you spent most resources on?"

## How to Read and Use a Job Graph

### Finding Unexpected Competitors
Study the Big Job your product competes for. Competitors are rarely who you think:
- Warehouse management app competes with Excel and paper notebooks
- Logistics management system competes with WhatsApp group chats
- Mattresses compete with coffee and sleeping pills

### Understanding Solution = Actions
Frequently, the "hired solution" is the person's own actions ("I did it myself"). This signals either:
- Small budget
- Person doesn't know other solutions exist
- Person knows solutions exist but doesn't know their value

### Reading the Critical Sequence
1. Map the full sequence of jobs from "orientation" to "getting value"
2. Identify where people DROP OFF
3. The EARLIEST drop-off point is where to focus effort
4. Remember: Big Job remains even after drop-off -- person goes to competing solution

### Graph Simplification Over Time
Over decades, products kill lower-level jobs. The graph simplifies. This is how value is created long-term. Only two mechanics work on a decades-long horizon:
1. Killing jobs (eliminating steps)
2. Moving to higher-level jobs (doing what the step was FOR, not the step itself)

Example: ChatGPT vs. Microsoft Word -- Word has thousands of features (jobs to learn), ChatGPT has ~10 buttons but writes the letter/dissertation/code for you. The graph was dramatically simplified.

## Anti-patterns in Building Job Graphs

### Anti-pattern: Trusting Future Intentions
**What**: Building a graph based on what people SAY they'll do in the future.
**Why wrong**: People are terrible at predicting their own future behavior.
**Instead**: Only include jobs the person has EXECUTED in the past (spent time/money/energy).

### Anti-pattern: Confusing Features with Value
**What**: Assuming more features = more value because you're "executing more jobs."
**Why wrong**: More jobs = more cost (time, energy, cognitive load). Value is about LESS total investment for the SAME or better result.
**Instead**: Ask "How can I make it so the person doesn't need to know these features exist?"

### Anti-pattern: Studying the Full Graph
**What**: Attempting to map every job for every person.
**Why wrong**: Massive waste of resources. For most business tasks, you need only small portions.
**Instead**: Determine your business task first, then identify which piece of the graph you need.

### Anti-pattern: Ignoring Graph Levels
**What**: Treating all jobs as equal regardless of their position in the hierarchy.
**Why wrong**: Higher-level jobs drive motivation and emotion; lower-level jobs are tactical and volatile.
**Instead**: Anchor strategy on Big Jobs and Core Jobs. Optimize at lower levels for execution efficiency.

### Anti-pattern: Building Graph Without Segmentation
**What**: Creating one job graph for "all customers."
**Why wrong**: Different segments have different jobs, different solutions, different graphs.
**Instead**: Build graphs per segment. Segment by past behavior on specific jobs.

### Anti-pattern: Ignoring the Consideration Set
**What**: Assuming the person will find and consider your solution naturally.
**Why wrong**: If your solution is not in the person's consideration set, they will never hire it regardless of its quality.
**Instead**: Map orientation jobs. Design activating knowledge delivery. Find the Big Job where competing solutions already exist in the consideration set, and compete THERE.

## B2C vs B2B Interview Guides

### B2C Structure (v3.2)
Split into two flows based on the main job type:
1. **Frequency jobs flow**: e.g., "run a marketing campaign", "buy groceries", "manage symptoms"
2. **Sequential jobs flow**: e.g., "take a mortgage to buy an apartment"

Guide modules (mix and match per business task):
- Navigation into jobs (new block -- quickly map jobs in ~10 minutes)
- Deep study of the job (full question set, select as needed)
- Previous and next versions of the job
- Navigation into lower-level jobs (toggle: frequency or sequential)
- Solution interview (optional -- if you have an offer to test)

### B2B Structure (v3.3)
Same core structure plus:
- Qualifying questions block (unique per product, important but not standardized)
- Job graph study block (same frequency/sequential split)
- Roles, deal structure, budget, recommenders block
- Optional study of "our specific work/solution" block
- Optional solution interview block

Budget: 45-60-90 minute interview. Choose blocks based on business task.

### Key Addition in Both: Activating Knowledge Question
New question: "What did you learn/discover that made you want to [do this job]?"
Example response: "My sister took a mortgage and I realized it's not scary."
This reveals the activating knowledge that triggered the job, which becomes the basis for marketing messaging and value communication.

### Key Addition: Expected Result Criteria
New question: "What criteria for the expected result do you need?"
Reveals: fast, cheap, reliable, safe, prestigious, by a specific deadline, guaranteed outcome. These criteria differ by segment and directly inform value proposition design.

---

## Additional Knowledge from Workshop 1 (w01)

### The Work -> Solution -> Problem Causal Chain

**Procedural rule**: Problems NEVER exist in a vacuum. A problem is always a derivative of a specific person hiring a specific solution for a specific job, and that solution underperforming.

**Definition of Problem (Zamesin)**: A problem is a brain signal that a predicted outcome did not materialize. The brain predicted that the solution would execute the job adequately; the prediction was not confirmed. The person expected X, got less than X.

**How to describe any problem completely**:
1. State the JOB (what goal the person wanted to accomplish)
2. State the SOLUTION hired (what the person actually used to accomplish the job)
3. State the PROBLEM (how the solution underperformed expectations)

**Example**: Job: "Incorporate my company correctly in Indonesia to minimize tax liability." Solution: "Legal Indonesia agency." Problem: "They incorrectly structured the company, resulting in a million rubles of unexpected tax liability plus two months of rework."

**Anti-pattern**: Describing a problem without its job and solution context. Statements like "users experience slow page loads" are incomplete -- the full chain must include the job being executed and the solution hired.

### Solutions Are Interchangeable

A core principle that must be internalized: people do NOT need your product. They need their jobs executed and their needs satisfied. All solutions for the same job are interchangeable.

**Implication for product thinking**: The shift is FROM "I build features" / "I build product" TO "I more effectively execute the jobs of my clients." This reframing opens up radically different solution spaces.

**Example**: Person stuck in Beijing traffic, needs to arrive on time for a meeting. Solution hired: personal car on public roads. Problem: stuck in traffic, will be late. Alternative solution: $60 service where two people arrive on a moped, one takes your car, you ride the moped through traffic. Without thinking in jobs, this solution is invisible. With jobs thinking, it is an obvious option.

### B2B: Personal Job Is the Primary Motivator

In B2B, for every decision-maker (LPR), business stakeholder, and some end users, there are ALWAYS two jobs:

1. **Business job**: What is in my official goals, or what my manager expects from me. ("Increase ad buying volume", "Reduce theft percentage", "Launch new product")
2. **Personal job**: What I personally want to get from accomplishing the business job. ("Not get fired", "Get promoted", "Feel safe", "Prove I'm competent")

**Critical insight**: The personal job is the NECESSARY AND SUFFICIENT condition for hiring a solution. The business job is only a NECESSARY condition.

**Decision rule**: If you know and execute the personal job well, you will be the FIRST product the person considers when looking for a solution. If you only know the business job, you compete on features with everyone else.

**Example**: Farm equipment buyers in Kazakhstan. Business job: "Ensure workers are available for sowing, pest control, harvest." Personal job: "Stop worrying about constant staffing headaches -- workers who drink, steal, damage equipment, don't show up." A product that addresses the personal job (removes the headache) wins decisively over one that only addresses the business job (provides labor management tools).

---

## Additional Knowledge from Workshop 2 (w02)

### Refined Core Job and Big Job Definitions (Product-Relative)

The existing definitions describe Core Job and Big Job from the graph's abstract perspective. Workshop 2 introduces a critical refinement -- these terms are RELATIVE TO YOUR PRODUCT:

**Core Job(s)**: The highest-level job(s) that your solution FULLY executes for the person. These are jobs your product practically completely accomplishes.

**Big Job(s)**: The job(s) one level ABOVE Core Jobs -- the jobs for which Core Jobs are executed, but which your solution does NOT fully execute. Big Jobs define the true competitive landscape because they include jobs fulfilled by competing solutions.

**Alternative framing** (from later in Workshop 2): Big Job = the job your solution executes INCOMPLETELY. Core Job = the job below Big Job that your product fully executes.

**Practical test for distinguishing levels**:
- Ask: "Does our product fully accomplish this job for the person?" If YES -> this is a Core Job candidate.
- Ask: "Is there a higher-level job that this Core Job serves, which our product does NOT fully accomplish?" If YES -> that higher-level job is the Big Job.

**Example -- Personal branding service (LiFT)**:
- Big Job: "Build my personal brand as a top manager"
- Core Jobs the product executes: attract subscribers, create PR strategy
- Jobs the product does NOT execute (person does themselves): run a blog, photoshoots
- Competitive landscape defined by Big Job: PR agencies, marketing consultants, personal coaches -- not just other branding services

**Example -- Biorg.Kadry (B2B HR automation)**:
- For HRD role: Big Jobs = "Quickly onboard employees without errors" + "Reduce compliance violation risks"
- For HRD role: Core Jobs = "Quickly enter new hire data" + "Reduce data entry errors"
- For Decision Maker (LPR): Big Jobs = "Quickly onboard employees" + "Save hiring budget"
- For Decision Maker (LPR): Core Jobs = "Quickly process hiring documents" + "Save budget on data entry"
- Value propositions derived: "60% faster document processing" (for HRD), "60-70% of recruiter time freed" (for LPR)

### Moving to a Higher-Level Job (Product Paradigm Shift)

This is the most powerful strategic move: instead of executing lower-level jobs better, ELIMINATE them by moving your product to compete at the higher-level job.

**Procedure**:
1. Map the current sequential jobs your product helps execute
2. Identify the higher-level job these sequential jobs serve
3. Ask: "Can we skip intermediate jobs and directly deliver the higher-level job result?"
4. If yes, you kill multiple lower-level jobs at once

**Verification question**: "Are there competitors who deliver the result 'turnkey' (pod klyuch), while I only deliver one component of the result?"

**Stopping criterion**: Stop moving up when at the next level up there are NO competitors executing that job. That level is too abstract for competition.

**Example -- Yandex Arenda vs. CIAN**:
- CIAN executes one lower-level job: "Post a listing" (within the sequence: understand the market -> photograph apartment -> post listing -> show apartment -> sign contract)
- Yandex Arenda moved to the higher-level job: "Rent out the apartment" -- executing/killing almost all lower-level jobs (market research, photography, listing, showing)
- Result: Yandex Arenda competes at a fundamentally different level, justified charging more, and reduced the graph dramatically

**Example -- LiFT personal branding**:
- Average check X3 by moving to the higher-level job "Build personal brand" instead of executing individual lower-level jobs (PR, strategy, attract subscribers, photoshoots)

### Business Jobs (Jobs of Your Business/Product)

Jobs exist not only for customers but also for the product/business itself.

**Definition**: Business jobs are jobs whose execution allows your business to receive business value.

**Key insight**: A single product feature/system can serve MULTIPLE jobs from DIFFERENT stakeholders simultaneously -- some are customer jobs, some are business owner jobs.

**Example -- LMS for Zamesin's course**:
- Customer job: "Access course materials" -> Solution: LMS platform
- Zamesin's job: "Reduce piracy percentage" -> Solution: Authorization + Kinescope video hosting
- Zamesin's job: "Improve course materials" -> Solution: Analytics within LMS
- All three jobs are served by the SAME LMS system, but they belong to different stakeholders

### Critical Sequence and Segment/Subsegment Relationship

Different segments and subsegments have DIFFERENT critical sequences for the same Big Job.

**Example -- Figma users** (Big Job: "Develop new app functionality"):
- Subsegment 1 (solo designer + developer, no feedback): Critical sequence = Draw mockup -> Hand off to development (2 steps)
- Subsegment 2 (team with manager feedback, no UX testing): Critical sequence = Draw mockup -> Refine by feedback -> Hand off to development (3 steps)
- Subsegment 3 (portfolio designer): Critical sequence = Draw mockup -> Test prototype in UX tests -> Refine by feedback (3 steps, different jobs)

**Implication**: Figma's product evolution was driven by progressively executing MORE jobs in the critical sequence:
1. First: Draw mockup (core drawing tool)
2. Then: Comments + calls in Figma (killed "refine by feedback" via external tools)
3. Then: Prototypes + interactivity (killed "test prototype" via external tools)
4. Then: Dev mode (killed "hand off to development" via external tools)

Each step expanded which subsegments could fully execute their critical sequence within Figma.

### Two Strategic Priorities Using Critical Sequences

**Priority 1 -- For growing metrics within a segment**: Execute Core Jobs MORE EFFECTIVELY in the critical sequences of focus segments and subsegments.

**Priority 2 -- For scaling to new segments**: Focus on segments/subsegments where your product can ALREADY execute Core Jobs in their critical sequences. The first scaling priority is to find segments whose critical sequences your product already covers.

**Decision heuristic for unfulfillable critical sequences**: A person may NOT hire your solution if they KNOW that other jobs in the critical sequence (which your product does not cover) will not be executed. They will switch to an alternative solution for the Big Job that has a critical sequence they CAN complete -- even if the result is worse.

**Example**: Styling service. Big Job: "Buy clothes." Critical sequence with stylist: delegate outfit selection -> buy -> correctly combine outfits. If the person knows that "correctly combine outfits" (step 3) won't be executed by the stylist, they may abandon the stylist and just buy clothes themselves -- the result is worse, but the critical sequence completes.
