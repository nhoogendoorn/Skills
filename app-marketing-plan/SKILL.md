---
name: app-marketing-plan
description: "Create a comprehensive app marketing plan producing four deliverable files: marketing plan (including paywall strategy, app store optimization, and content marketing), monetization plan (pricing, tiers, paywall strategy), design brief (marketing visuals direction), and tone of voice guide. Use when the user wants to plan marketing for a mobile app, create an app launch strategy, define app monetization and pricing, optimize app store presence, develop brand voice, plan paywall and upgrade flows, or create a go-to-market plan. Triggers: 'app marketing plan', 'marketing strategy for my app', 'app launch plan', 'monetization strategy', 'app store optimization plan', 'paywall strategy', 'app pricing plan', 'tone of voice for my app', 'design brief for app marketing'."
---

# App Marketing Plan

Create a complete app marketing strategy grounded in minimalist entrepreneur philosophy: community-first, value-before-ask, charge-something-always, spend-time-before-money.

This skill produces 4 deliverable files:
1. `tone-of-voice.md` -- Brand voice guide (written first, informs all other docs)
2. `monetization.md` -- Pricing, tiers, paywall strategy, financial math
3. `marketing.md` -- Go-to-market, content strategy, ASO, copywriting direction
4. `design-brief.md` -- Visual direction for marketing materials

---

## Context Gathering

Before generating deliverables, gather the following. If `.agents/product-marketing-context.md` or `.claude/product-marketing-context.md` exists, read it first and only ask for gaps.

### 1. App & Product
- App name and platform (iOS, Android, or both)
- App Store category
- Core problem it solves (in one sentence)
- 3-5 key features
- Current stage: idea, MVP, launched (how many users/customers?)
- Competitor apps (2-3 names)

### 2. Audience & Community
- Target user persona (role, age range, context)
- Communities they belong to (subreddits, Discord servers, forums, Slack groups)
- Where they gather online and offline
- Language they use to describe their problem
- What they have tried before (alternative solutions)

### 3. Business Model
- Current pricing (if any)
- Competitor pricing (range)
- Monthly revenue target
- Cost structure (hosting, tools, time)
- Desired model: subscription, one-time purchase, freemium, or undecided

### 4. Marketing Context
- Current marketing channels (if any)
- Existing audience size (social, email)
- Content the founder can create (writing, video, audio, design)
- Comfort level with building in public
- Where traffic will come from initially

### 5. Brand & Voice
- 3-5 brand personality adjectives (e.g., friendly, direct, playful, expert)
- Formality level: casual, conversational, professional, or formal
- Competitor brands they admire (for tone reference)
- Competitor brands they want to differentiate from

---

## Deliverable Pipeline

Generate deliverables in this order. Each builds on the previous:

1. **tone-of-voice.md** first -- establishes writing style for all other documents
2. **monetization.md** second -- pricing decisions feed into marketing and paywall sections
3. **marketing.md** third -- the core plan, references monetization for paywall/pricing
4. **design-brief.md** last -- needs positioning and tone to be established first

Apply the tone-of-voice.md guide when writing all subsequent deliverables. Maintain consistent voice throughout.

---

## Deliverable 1: tone-of-voice.md

Generate a tone of voice guide that ensures consistent brand communication across app store listing, marketing content, in-app copy, and paywall screens.

For detailed voice/tone framework patterns, see [references/tone-of-voice-guide.md](references/tone-of-voice-guide.md).
For copywriting principles that inform voice, see [references/copywriting-guide.md](references/copywriting-guide.md).

### Output Structure

**Brand Personality**
- 3-5 adjectives, each with an operational definition (what it looks like in practice, not just the word)

**Voice Attributes**
- "We are / We are not" table with at least 5 pairs
- Each pair with a concrete example sentence

**Formality Level**
- Position on the spectrum (casual to formal) with example sentence at that level
- Comparison sentence at one level above and below to show the boundaries

**Writing Principles**
- 5-7 rules that enforce this voice. Draw from:
  - Clarity over cleverness
  - Benefits over features
  - Customer language over company language
  - Specificity over vagueness
  - Active over passive
  - Honest over sensational

**Vocabulary Guide**
- 10+ preferred words with what they replace
- 5+ banned words/phrases with why
- Jargon policy (when technical terms are acceptable)

**Tone Shifts by Context**
For each context, describe the tone adjustment:
- App store listing (confident, benefit-focused)
- In-app paywall (helpful, zero-pressure)
- Social media (authentic, educational)
- Email newsletter (personal, story-driven)
- Support/error messages (empathetic, solution-oriented)
- Landing page (clear, proof-heavy)

**Example Rewrites**
- Take 3 generic marketing sentences about the app and rewrite them in the brand voice
- Show the contrast between generic and branded

---

## Deliverable 2: monetization.md

Generate a monetization plan covering pricing, tier structure, paywall strategy, and financial viability.

For pricing models and frameworks, see [references/pricing-frameworks.md](references/pricing-frameworks.md).
For paywall patterns and experiments, see [references/paywall-patterns.md](references/paywall-patterns.md).

### Output Structure

**Pricing Model**
- Recommendation: cost-based, value-based, or hybrid with rationale
- Competitive pricing context (where this sits relative to competitors)
- Initial price point with reasoning

**Tier Structure**
- Free tier: what's included, what's gated, purpose (acquisition funnel)
- Paid tier(s): features, price, target segment
- Feature allocation logic: why each feature is free or paid
- Future tier potential (when to add premium/enterprise)

**Financial Independence Math**
- Monthly revenue target
- Price point x customers needed = timeline
- Worked calculation at realistic acquisition rate (1 customer/business day for early stage)

**Paywall Strategy**
- Recommended paywall type: feature lock, usage limit, or trial expiration (pick based on app model)
- Trigger points mapped to the app's aha moment
- Paywall screen components:
  - Headline (use formula: "Unlock [Feature] to [Benefit]")
  - Value demonstration approach
  - CTA text (value-oriented, not generic)
  - Escape hatch text
- Timing rules: when to show, when not to show
- Frequency: prompts per session, cool-down after dismiss

**A/B Testing Roadmap**
- Top 3 paywall experiments to run first (from [references/paywall-patterns.md](references/paywall-patterns.md) -- Experiment Ideas section)
- For each: hypothesis, what to test, success metric

**Pricing Evolution Plan**
- When to raise prices (signals to watch)
- When to add tiers
- When to revisit the model entirely

---

## Deliverable 3: marketing.md

Generate the core marketing plan including go-to-market strategy, content marketing, app store optimization, and copywriting direction.

For ASO best practices and scripts, see [references/aso-guide.md](references/aso-guide.md).
For copywriting principles and formulas, see [references/copywriting-guide.md](references/copywriting-guide.md).
For minimalist entrepreneur philosophy, see [references/minimalist-principles.md](references/minimalist-principles.md).

### Output Structure

**Positioning Statement**
One sentence: [App name] helps [target audience] [solve problem] by [unique approach], unlike [alternatives] which [limitation].

**Go-to-Market Strategy by Stage**

*Pre-Launch / First 100 Users:*
- Concentric circles sales: 10 friends/family, 10 community members, cold outreach template
- Manual, one-on-one selling (no ads, no launches)
- Build in public: what to share, where to share it
- Product-market fit signals to watch for

*Post-PMF (100+ customers):*
- Content marketing via educate/inspire/entertain framework:
  - 5 content ideas per level, specific to this app
- Primary platform recommendation (based on where audience gathers)
- Posting cadence (realistic, sustainable schedule)
- Email list strategy: lead magnet idea, collection method, email cadence
- Build in public plan: what milestones and learnings to share

*Scale (when organic traction is proven):*
- When to consider paid acquisition
- Lookalike audience strategy
- Spend on retention before acquisition
- Revenue-per-customer math for ad spend ceiling

**App Store Optimization**

*Metadata (write actual draft copy, respecting character limits):*
- Title (Apple: 30 chars, Google: 50 chars)
- Subtitle (Apple: 30 chars) / Short description (Google: 80 chars)
- Keyword field (Apple: 100 chars, comma-separated, no spaces, no plurals)
- Description excerpt (first 3 lines visible before "more" -- make them count)
- "What's New" template for updates

*Visual Assets:*
- Screenshot strategy: what to show in first 3 screenshots, caption approach
- Icon direction: what it should convey at 60x60px
- Preview video guidance: core value in first 5 seconds

*Reviews & Ratings:*
- When to prompt for ratings (after positive experiences)
- Review response strategy (24-48 hour target)
- How to use review insights for product iteration

*Launch/Update:*
- Pre-launch checklist (key items)
- Update cadence recommendation
- Seasonal opportunities relevant to this app category

For ASO analysis tools, run scripts from `scripts/` directory. See [references/aso-guide.md](references/aso-guide.md) -- Scripts Reference for available tools.

**Copywriting Direction**

*Headline options (3 alternatives using formulas from copywriting guide):*
- Formula: {Achieve outcome} without {pain point}
- Formula: {Question highlighting pain point}
- Formula: Turn {input} into {outcome}

*CTA recommendations:*
- Primary CTA: [Action Verb] + [What They Get]
- Secondary CTA option
- Weak CTAs to avoid for this app

*Landing page structure recommendation:*
- Recommended section order (from Page Structure Framework in copywriting guide)
- Which copywriting framework fits best (PAS/AIDA/StoryBrand) and why

**Minimalist Review Checkpoint**

Apply the decision framework to gut-check the entire marketing plan:

| Question | Assessment |
|----------|-----------|
| Does this serve the community? | [specific answer] |
| Is this the simplest approach? | [specific answer] |
| Am I spending time before money? | [specific answer] |
| Have customers asked for this? | [specific answer] |
| Does this improve profitability? | [specific answer] |

Flag anything that violates minimalist entrepreneur principles and suggest a simpler alternative.

---

## Deliverable 4: design-brief.md

Generate a design brief for app marketing visuals: app store screenshots, landing page, social media assets, and ad creatives.

### Output Structure

**Marketing Context**
- App positioning (from marketing.md)
- Target audience visual preferences
- Competitive visual landscape (what competitors look like, how to differentiate)

**Design Goals**
- 3-5 specific, measurable design goals (e.g., "Screenshots should communicate core value without reading captions")
- Design non-goals (what to explicitly avoid)

**Visual Direction**
- Aesthetic keywords (e.g., minimal, vibrant, premium, playful)
- Color strategy: primary, secondary, accent -- with rationale tied to brand personality
- Typography direction: serif/sans-serif, weight, personality
- Imagery style: photography, illustration, abstract, product-focused
- Iconography approach

**Design Principles**
- 3-5 principles ordered by priority
- Each with operational definition and example of how to apply
- Example: "Clarity first: If a screenshot needs a caption to make sense, redesign the screenshot."

**Platform-Specific Requirements**
- App Store screenshot dimensions and count
- Social media asset sizes (primary platform)
- Landing page visual requirements
- Ad creative dimensions (if applicable)

**App Store Screenshot Direction**
- Shot list: what each of the first 5 screenshots should show
- Caption approach: benefit-led, feature-led, or story-led
- Visual consistency rules across screenshots
- Device frame: yes/no, which device

**Decision Heuristics**
- When choosing between two visual approaches, how to decide
- Tied to brand personality and design principles

**Red Flags**
- Visual anti-patterns to avoid (cluttered screenshots, too much text, inconsistent style)
- Competitor visual cliches in this category to avoid

---

## Writing Rules for All Deliverables

Apply these rules when generating all 4 files:

1. **Apply tone-of-voice.md** -- Every deliverable should sound like the same brand. Use the vocabulary guide and writing principles.
2. **Be opinionated** -- The plan should help the user say "no" to misaligned choices. Don't hedge with "you could try X or Y" -- recommend and explain why.
3. **Be actionable** -- Every recommendation should specify what to do, not just what to consider. Include concrete examples, draft copy, specific numbers.
4. **Be specific to this app** -- Ground recommendations in the user's context. Generic advice like "post regularly on social media" is useless. Instead: "Post 3x/week on r/[subreddit] sharing [specific type of content]."
5. **Follow minimalist principles** -- See [references/minimalist-principles.md](references/minimalist-principles.md). Prefer simple over complex, time over money, selling over marketing, profitability over growth.
6. **Use customer language** -- Mirror the words and phrases the target audience uses, not marketing jargon.

---

## Validation Checklist

Before delivering, verify each file:

### tone-of-voice.md
- [ ] Voice attributes are consistent with stated brand personality
- [ ] Example rewrites clearly differ from generic tone
- [ ] Vocabulary guide has actionable preferred/banned words
- [ ] Tone shifts make sense for each context

### monetization.md
- [ ] Financial math adds up (price x customers = revenue target)
- [ ] Paywall strategy has specific trigger points tied to the app's aha moment
- [ ] Pricing has competitive context and rationale
- [ ] A/B testing experiments are specific and actionable

### marketing.md
- [ ] Strategy is stage-appropriate (not telling a pre-launch app to run ads)
- [ ] ASO metadata respects platform character limits
- [ ] Content ideas are specific to this app and audience
- [ ] Minimalist review checkpoint is filled in honestly
- [ ] Headline and CTA options use proven formulas

### design-brief.md
- [ ] Design principles don't contradict each other
- [ ] Visual direction aligns with tone of voice
- [ ] Screenshot direction is specific (not "show the app")
- [ ] Platform dimensions are accurate

### Cross-Deliverable Consistency
- [ ] Tone of voice from deliverable 1 is evident in deliverables 2-4
- [ ] Pricing from monetization.md matches pricing mentions in marketing.md
- [ ] Design brief visual direction aligns with brand personality from tone-of-voice.md
- [ ] Paywall copy in monetization.md follows copywriting principles from marketing.md

---

## Resources

### Reference Files
- [references/copywriting-guide.md](references/copywriting-guide.md) -- Headline formulas, CTA guidelines, page structure, PAS/AIDA/StoryBrand frameworks. Consult when writing marketing.md copywriting sections and tone-of-voice.md writing principles.
- [references/paywall-patterns.md](references/paywall-patterns.md) -- Paywall types, templates, timing rules, anti-patterns, experiment ideas. Consult when writing monetization.md paywall strategy.
- [references/aso-guide.md](references/aso-guide.md) -- Platform requirements, keyword research, metadata optimization, visual assets, scripts reference. Consult when writing marketing.md ASO section.
- [references/pricing-frameworks.md](references/pricing-frameworks.md) -- Pricing models, tier progression, financial math, sales strategy. Consult when writing monetization.md pricing sections.
- [references/minimalist-principles.md](references/minimalist-principles.md) -- The 8 principles, decision framework, community-first foundation, marketing philosophy. Consult when writing marketing.md go-to-market and review checkpoint.
- [references/tone-of-voice-guide.md](references/tone-of-voice-guide.md) -- Voice vs. tone framework, formality spectrum, context-specific tone shifts. Consult when writing tone-of-voice.md.

### ASO Analysis Scripts
Located in `scripts/`. Run with Python 3. See [references/aso-guide.md](references/aso-guide.md) -- Scripts Reference for details.
- `keyword_analyzer.py` -- Keyword research and analysis
- `metadata_optimizer.py` -- Metadata optimization with character validation
- `competitor_analyzer.py` -- Competitor ASO analysis
- `aso_scorer.py` -- ASO health score calculation
- `ab_test_planner.py` -- A/B test planning and tracking
- `localization_helper.py` -- Multi-language optimization
- `review_analyzer.py` -- Review sentiment analysis
- `launch_checklist.py` -- Pre-launch validation
