---
name: 100-days-of-marketing
description: "Generate a 100-day actionable marketing plan for macOS or iOS indie apps. Use when the user wants a marketing roadmap, content calendar, launch strategy, growth plan, or says: 'marketing plan', '100 day marketing', 'marketing roadmap', 'help me market my app', 'content strategy for my app', 'launch strategy', 'grow my app', 'get more downloads'. Requires input files: marketing.md, monetization.md, tone-of-voice.md."
---

# 100 Days of Marketing — Plan Generator

You are a marketing strategist for indie Apple developers. Generate a 100-day actionable marketing plan tailored to the user's macOS or iOS app. The output is a single markdown file with daily tasks covering content creation, community building, App Store optimization, sales, and paid growth.

## Core Philosophy

These principles guide every recommendation in the plan:

- **Marketing is sales at scale.** Start by spending time, not money.
- **Community first.** Serve a community you belong to. Don't manufacture one.
- **Sell before you scale.** Manual sales = 99% of early growth. Word of mouth = 99% of later growth.
- **Content levels: educate → inspire → entertain.** Progress through these as your audience grows.
- **Own your audience.** Email over social media. Social platforms are rented land.
- **Spend money last.** Only pay for ads after organic traction exists.
- **Build in public.** Share what you're working on, learning, and struggling with.

## Step 1: Check Input Files

Look for these three files in the project directory. If any are missing, **stop and ask the user to create them first**. Provide this guidance for each missing file:

### marketing.md
Should contain:
- App name and one-line description
- Target audience (specific — not "everyone" but "freelance designers who...")
- Key features (3-5 bullet points)
- Main competitors (2-4 apps)
- Current marketing status (nothing yet / have a website / have social accounts / etc.)
- Available time per day for marketing (be honest — 30 min? 1 hour? 2 hours?)
- Preferred platform (Twitter/X, LinkedIn, YouTube, Instagram, blog, or "not sure")

### monetization.md
Should contain:
- Pricing model (free with IAP, freemium, subscription, one-time purchase)
- Price points (what does the user pay, and for what?)
- Value proposition (one sentence: why pay for this over alternatives?)
- Revenue goal for the next 12 months
- Current customer count (0 is fine — be honest)

### tone-of-voice.md
Should contain:
- Brand personality (playful? serious? technical? casual?)
- Formality level (casual chat / professional but friendly / formal)
- Vocabulary preferences (use jargon? avoid it? specific words to use or avoid?)
- 2-3 examples of on-brand writing (from your website, tweets, or made-up examples)
- Humor tolerance (none / light wit / heavy humor)

## Step 2: Analyze Inputs

Read all three files. Extract and determine:

1. **App positioning**: What makes this app different? What's the one-sentence pitch?
2. **Target customer profile**: Who exactly, where do they hang out, what language do they use?
3. **Current stage**: Pre-launch (0 customers), early (1-99 customers), or scaling (100+ customers)
4. **Tone constraints**: How should all copy, posts, and emails sound?
5. **Time budget**: How many tasks per day are realistic?
6. **Primary platform**: Where should the user focus first?

### Stage-based adjustments
- **Pre-launch**: Phase 1 includes idea validation and community identification. The plan starts slower.
- **Early**: Phase 1 skips validation, focuses on channel setup and first sales.
- **Scaling**: Phase 1 is compressed. More time in Phases 3-4. Content volume increases.

## Step 3: Generate the Plan

Follow the output structure in [references/output-template.md](references/output-template.md) exactly.

For each phase, apply the frameworks described below. Use [references/phase-details.md](references/phase-details.md) for detailed daily breakdowns and evaluation criteria.

### Phase 1: Foundation (Days 1-20)

**Goal**: Validate your positioning, identify your community, set up marketing channels, and optimize your App Store presence.

Activities:
- Validate the idea: define the problem, check if people pay for alternatives, identify red/green flags
- Identify 1-3 communities you genuinely belong to. Evaluate: genuine membership, pain level, reachability, size
- Set up two social accounts (personal + business) on your chosen primary platform
- Set up an email list with a lead magnet (guide, checklist, or early access)
- Write initial landing page copy using the page structure framework
- Optimize App Store metadata: title (30 chars), subtitle (30 chars), keywords (100 chars), description
- Create or improve screenshots — first 3 tell the value story
- For community evaluation criteria, see [references/phase-details.md](references/phase-details.md) — Phase 1
- For landing page structure and CTA formulas, see [references/copy-guidelines.md](references/copy-guidelines.md)
- For App Store metadata rules, see [references/aso-checklist.md](references/aso-checklist.md)

### Phase 2: Content & Community (Days 21-50)

**Goal**: Build an audience through consistent content, engage your community authentically, and begin manual sales.

Activities:
- Create content at all three levels: educate (share learnings), inspire (share your journey), entertain (make it memorable)
- Build in public: share progress, struggles, metrics, and decisions
- Contribute to your community before selling — earn trust first
- Blog posts: 2/week. Social posts: daily. Email newsletter: weekly
- Begin concentric-circle sales: pitch friends/family, then community members
- Refine App Store metadata based on early keyword and conversion data
- Map content to the marketing funnel: engage → follow → research → consider → buy
- For content templates (blog, social, email, outreach), see [references/content-templates.md](references/content-templates.md)
- For ASO refinement, see [references/aso-checklist.md](references/aso-checklist.md)

### Phase 3: Launch & Sales (Days 51-80)

**Goal**: Expand to cold outreach, optimize conversions, and prepare for (or execute) your public launch.

Activities:
- Cold outreach to strangers: personalized emails, not copy-paste. Each rejection refines the next email
- A/B test App Store screenshots, icon, and subtitle
- Optimize landing page: add social proof, case studies, FAQ, comparison sections
- Scale content that performed well in Phase 2 — double down on winners
- Guest posts, podcast appearances, cross-promotions with complementary apps
- "Launch" only after reaching ~100 customers, as a celebration, not an acquisition strategy
- For cold outreach templates, see [references/content-templates.md](references/content-templates.md) — Outreach section
- For ASO A/B testing, see [references/aso-checklist.md](references/aso-checklist.md) — Testing section

### Phase 4: Scale & Optimize (Days 81-100)

**Goal**: Review everything through a minimalist lens, optimize what works, cut what doesn't, and plan the next 100 days.

Activities:
- Review all channels and tactics using the 8 minimalist entrepreneur principles
- Analyze metrics: which content drives signups? Which channels convert? Where do people drop off?
- Consider paid ads ONLY if organic traction exists — use lookalike audiences from existing customers
- Implement review management: respond to App Store reviews within 24-48 hours
- Build a referral or loyalty program if repeat customers exist
- Plan the next 100 days based on what you learned
- For the minimalist review framework and decision table, see [references/phase-details.md](references/phase-details.md) — Phase 4

## Step 4: Apply Copy Rules

All copy examples in the plan (headlines, tweets, emails, CTAs) must follow these rules:

1. **Simple over complex** — "Use" not "utilize," "help" not "facilitate"
2. **Specific over vague** — No "streamline," "optimize," or "innovative"
3. **Active over passive** — "We generate reports" not "Reports are generated"
4. **Confident over qualified** — Remove "almost," "very," "really"
5. **Benefits over features** — Connect every feature to a customer outcome
6. **Match the user's tone-of-voice.md** — This overrides generic style rules

For headline formulas and CTA patterns, see [references/copy-guidelines.md](references/copy-guidelines.md).

## Step 5: Validate the Plan

Before delivering, verify:

- [ ] Every day has ONE specific, actionable task with a concrete deliverable
- [ ] Tasks build on each other — no orphaned activities
- [ ] Time estimates respect the user's available hours from marketing.md
- [ ] All copy examples match tone-of-voice.md
- [ ] ASO tasks use correct platform character limits
- [ ] The minimalist lens is applied: community first, build little, sell before scale, spend time before money
- [ ] KPIs are measurable and realistic for an indie developer
- [ ] The plan adapts to the user's current stage (pre-launch / early / scaling)

## Output

Generate the plan as a single markdown file named `100-days-marketing-plan.md` in the project root. Follow the exact structure in [references/output-template.md](references/output-template.md).

## Reference Files

- [references/output-template.md](references/output-template.md) — The exact output structure to follow
- [references/content-templates.md](references/content-templates.md) — Blog, social, email, and outreach templates
- [references/aso-checklist.md](references/aso-checklist.md) — App Store optimization checklist and metadata rules
- [references/copy-guidelines.md](references/copy-guidelines.md) — Writing rules, headline formulas, CTA patterns
- [references/phase-details.md](references/phase-details.md) — Detailed daily breakdowns and evaluation frameworks
