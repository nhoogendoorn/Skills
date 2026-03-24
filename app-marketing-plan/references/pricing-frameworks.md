# Pricing Frameworks

## Table of Contents

1. Core Principle
2. Pricing Models
3. Psychology of Pricing
4. Pricing Principles
5. Initial Price Setting
6. App Store Pricing Considerations
7. Monetization Models: Subscriptions vs Lifetime vs Consumables
8. Financial Independence Math
9. Tiered Pricing Design
10. Revenue Optimization Strategies
11. Concentric Circles Sales Strategy
12. Common Pricing Mistakes
13. When to Revisit Pricing

---

## 1. Core Principle

**Charge something. Always.** There is a massive difference between free and $1. Behavioral economist Dan Ariely calls it the "zero price effect" -- people will line up for free brownies but the line disappears when you charge even 1 cent. If you don't charge, you can't learn what customers actually value, and you can't sustain your business.

This principle matters more than most founders realize. Free users behave fundamentally differently from paying users. Free users churn at higher rates, submit more support requests per dollar of value, and provide less useful feedback because they have no skin in the game. A paying customer -- even one paying $1 -- has made a psychological commitment. They will use your product more deliberately, report bugs more constructively, and tell you honestly when something doesn't work.

The corollary: if nobody will pay you even $1, that is critical market signal. It means either your product doesn't solve a real problem, you're targeting the wrong audience, or your positioning fails to communicate the value. All of those are things you need to learn as early as possible.

---

## 2. Pricing Models

### Cost-Based Pricing

Calculate your costs and add a margin. This is the simplest model and works well when costs are predictable.

- **How it works**: Sum your per-unit costs (hosting, bandwidth, payment processing fees, support time, infrastructure) and add a margin of 20-50%.
- **Example**: A retail store buys wholesale at $25 and sells at $50 (50% margin). A SaaS product that costs $3/month per user in infrastructure might charge $9-15/month.
- **Best for**: Products with clear, measurable per-unit costs. Physical goods, API services billed by usage, infrastructure tools.
- **Limitation**: This model leaves money on the table for software products where the marginal cost of serving one more customer is near zero. If your product saves a business $500/month and you price it at $15 because that's cost-plus-margin, you're drastically undercharging.

### Value-Based Pricing

Price based on the value your product delivers to the customer, not what it costs you to deliver it.

- **How it works**: Identify what problem you solve, quantify its cost to the customer (in time, money, or frustration), and price as a fraction of that value.
- **Example**: Notion charges $10/user/month for Team plans. The cost to serve one user is pennies, but the productivity gain of having a shared workspace justifies the price many times over. Netflix charges extra for 4K and multi-screen -- features that cost them virtually nothing but that users value highly.
- **Best for**: Software, digital products, apps that save time or increase productivity. Nearly all successful indie apps use value-based pricing.
- **The 10x rule**: A common heuristic is to charge roughly 1/10th of the value you deliver. If your app saves someone 5 hours per month and their time is worth $50/hour, that's $250 of value -- a $25/month price point is reasonable.

### Hybrid Pricing

Most successful apps use a combination. Cost-based pricing sets your floor (you must cover costs), and value-based pricing sets your ceiling (what the market will bear). Your actual price sits somewhere between.

---

## 3. Psychology of Pricing

Understanding how people perceive prices is just as important as the number itself.

### Anchoring

People evaluate prices relative to the first number they see. If your pricing page shows a $29/month plan first, everything else is judged against that anchor. This is why many SaaS products list their most expensive plan first (left to right) or display a "Compare to" price.

**App example**: Fantastical shows its premium plan at $6.99/month but presents the annual price ($4.75/month billed annually) right next to it. The monthly price anchors high, making the annual price feel like a deal.

### The Decoy Effect

When people choose between two options, adding a third "decoy" option can shift preference toward the one you want them to pick. The decoy is intentionally unattractive compared to the target option.

**Classic example**: The Economist once offered: (A) Web-only for $59, (B) Print-only for $125, (C) Print + Web for $125. Nobody chose B, but its presence made C look like an incredible deal. Without B, most people chose A.

**App example**: If you offer a Basic plan at $4.99/month and a Pro plan at $14.99/month, adding a "Plus" plan at $12.99/month with only marginally more features than Basic makes Pro look like the obvious choice for just $2 more.

### Charm Pricing

Prices ending in 9 or 99 consistently outperform round numbers in conversion tests. $9.99 feels meaningfully cheaper than $10.00 to most people, even though the difference is a penny. This is well-documented across decades of retail research.

**App Store context**: Apple's price tiers are built around this. The standard tiers are $0.99, $1.99, $2.99, $4.99, $9.99, etc. Use them -- they exist because they work.

### Price Framing

How you present the price changes perception dramatically:

- **Daily framing**: "$0.33/day" feels trivial. "Less than a cup of coffee per week."
- **Annual savings**: "Save 40% with annual billing" reframes the annual plan as a discount rather than a large upfront cost.
- **Per-feature framing**: "Unlimited projects for just $3 more/month" isolates the upgrade cost to a single compelling feature.

**App example**: Bear (the writing app) charges $2.99/month or $29.99/year. The annual price is framed as "Save over 15%" and works out to about $0.08/day -- less than almost anything else you spend money on.

### Loss Aversion

People feel losses more acutely than equivalent gains. Free trials exploit this: after 7-14 days of using a product, canceling feels like losing something. This is why free trials convert better than "buy now" for most apps. The user has already integrated the product into their workflow.

---

## 4. Pricing Principles

1. **Start low, raise over time.** Prices naturally go up as products improve. Early customers get a deal -- they took a risk on you when you were unproven. Raising prices later is expected and healthy. Grandfather early customers at their original price to build loyalty.

2. **Pricing is not permanent.** Treat it as another variable to iterate on. Most indie developers agonize over the "right" price for weeks. Instead, pick something reasonable, ship it, and learn. You will adjust. Basecamp has changed their pricing model multiple times over 20 years.

3. **Tiered pricing is the goal.** Like plane tickets -- economy, business, first class. Same destination, different experience. Tiers let you capture value from different customer segments without leaving money on the table. A student and a professional will pay very different amounts for the same tool.

4. **The zero price effect.** Never give your product away for free as your default model. Even $1 creates a completely different dynamic. Free users and paying users are different populations with different behaviors and expectations.

5. **Free trials are table stakes.** Customers now open six tabs and compare immediately. Offer trials, but always with a clear path to paid. The trial should be long enough to reach the "aha moment" but short enough to create urgency. 7 days for simple tools, 14 days for more complex products.

6. **Don't confuse marketing with giving away your product.** Ad-driven models train users to expect free. Once you've established that expectation, it's extremely difficult to start charging. Build the paid model from day one.

---

## 5. Initial Price Setting

### The Four Questions

Before setting a price, answer these honestly:

**1. What are your variable costs per unit/customer?**
For a typical indie app: Apple's 15-30% commission, server costs per user, any third-party API costs (e.g., OpenAI API calls), payment processing for non-App Store purchases. Most indie apps have near-zero marginal costs, which means your floor is very low.

**2. What are competing or alternative solutions charging?**
Survey 5-10 competitors or alternatives. Note their pricing tiers, what features are in each tier, and how they position themselves. Don't just match competitors -- understand whether they are underpricing (common in crowded markets) or overpricing (common for legacy products coasting on brand).

**3. What would make this a "no-brainer" purchase for your ideal customer?**
This question forces you to think from the customer's perspective. If your task manager saves a freelancer 3 hours per week and they bill at $75/hour, that's $225/week of value. At $5.99/month, it's an absurd bargain. At $29.99/month, it's still a no-brainer. At $99/month, it starts to require justification.

**4. What price lets you be profitable from customer #1?**
This is the minimalist entrepreneur test. If each customer contributes positive margin from day one, you have a sustainable business at any scale. You don't need venture capital or hockey-stick growth. You need customers who pay more than they cost to serve.

### Competitive Pricing Benchmarks (Indie Apps, 2025)

| Category | Typical Monthly | Typical Annual | Examples |
|---|---|---|---|
| Simple utility | $1.99-4.99 | $9.99-29.99 | One-purpose tools, converters |
| Productivity | $4.99-9.99 | $29.99-59.99 | Bear, Things, GoodNotes |
| Professional tool | $9.99-19.99 | $59.99-149.99 | Fantastical, Cardhop, Ulysses |
| Team/Business | $9.99-29.99/user | $99.99-299.99/user | Notion, Linear, Slack |
| AI-powered | $9.99-29.99 | $79.99-199.99 | Apps with ongoing API costs |

---

## 6. App Store Pricing Considerations

### Apple's Price Tier System

Apple provides ~200 price points across 175 storefronts. Key tiers that matter for indie apps:

- **Tier 1 ($0.99)**: The impulse buy tier. Use for very simple utilities or as a one-time tip jar.
- **Tier 3 ($2.99)**: The sweet spot for simple paid-upfront apps. Low enough to be an impulse buy, high enough to signal value.
- **Tier 5 ($4.99)**: Common for higher-quality one-time purchases. GoodNotes, Procreate (before going subscription).
- **Tier 10 ($9.99)**: The standard monthly subscription tier for serious indie apps.
- **Custom tiers**: Apple now allows custom pricing in 0.10 increments in many regions. Use this for precision pricing.

### Subscription Pricing on the App Store

Apple takes a 30% commission in year one, dropping to 15% for subscribers who renew past 12 months (the Small Business Program also applies the 15% rate for developers earning under $1M/year). Factor this into your pricing:

- If you charge $9.99/month, you receive ~$7.00 in year one and ~$8.49 after year one (at 30%/15%).
- If you're in the Small Business Program, you receive ~$8.49 from day one.

**Introductory offers**: Apple supports three types:
- **Free trial**: No charge for X days/weeks/months. The most common and generally highest-converting option. 7-day trials are standard for simple apps; 14-30 days for complex tools.
- **Pay as you go**: Reduced price for X periods (e.g., $0.99/month for 3 months, then $9.99/month). Good for habit-forming apps where you need extended onboarding.
- **Pay up front**: One discounted payment for X periods (e.g., $4.99 for 3 months, then $9.99/month). Less common but useful for seasonal promotions.

**Promotional offers**: Available for existing or lapsed subscribers. Use these to win back churned users ("Come back for 50% off your first 3 months").

**Offer codes**: Generate redeemable codes for marketing campaigns, influencer partnerships, or customer service recovery. Limited to 10 million codes per app per quarter.

### Annual vs Monthly Pricing

The standard discount for annual billing is 15-20% off the monthly rate. Common patterns:

- $4.99/month / $29.99/year (50% savings -- aggressive, used for acquisition)
- $9.99/month / $79.99/year (33% savings -- moderate)
- $9.99/month / $99.99/year (17% savings -- mild, maximizes revenue per user)

Annual plans dramatically improve your cash flow and reduce churn (people are less likely to cancel mid-year). Many successful indie developers make the annual plan the default selection on their paywall.

---

## 7. Monetization Models: Subscriptions vs Lifetime vs Consumables

### Subscriptions

**When to use**: Your app delivers ongoing value, requires server infrastructure, or is regularly updated with new features.

**Advantages**: Predictable recurring revenue, aligns incentives (you must keep delivering value), preferred by Apple (they promote subscription apps more heavily), builds compounding revenue.

**Disadvantages**: Higher friction at point of purchase, subscription fatigue among users, requires continuous feature development to justify ongoing charges.

**Examples**: Todoist ($4/month Pro), Bear ($2.99/month), Ulysses ($5.99/month), Fantastical ($6.99/month).

### Lifetime / One-Time Purchase

**When to use**: Your app is primarily a tool that works offline, doesn't require significant ongoing server costs, and has a clear, bounded feature set.

**Advantages**: Lower friction, no "subscription fatigue" objection, simpler to communicate value, appeals to price-sensitive users who want to "own" their software.

**Disadvantages**: No recurring revenue (you need constant new customer acquisition), difficult to fund ongoing development, creates pressure to ship paid upgrades or new versions.

**Examples**: Things 3 ($49.99 one-time on Mac), Procreate ($12.99 one-time before their model change), Halide ($29.99 one-time or subscription).

**The hybrid approach**: Offer both. Many indie apps now offer a monthly subscription, an annual subscription, and a lifetime purchase at 3-5x the annual price. This captures different customer segments: the lifetime price appeals to long-term users and generates upfront cash, while subscriptions provide recurring revenue.

**Typical lifetime pricing**: 2.5x to 5x the annual price. If your annual plan is $49.99, a lifetime purchase at $149.99-$249.99 is reasonable. Set it high enough that you don't regret it when the customer is still using the app 5 years later.

### Consumables (Credits, Tokens)

**When to use**: Your app has variable per-use costs (AI API calls, image generation, cloud processing) or the usage pattern is highly variable across users.

**Advantages**: Aligns cost with usage, low barrier to entry, users pay for what they use.

**Disadvantages**: Unpredictable revenue, harder for users to budget, adds complexity to the user experience.

**Examples**: ChatGPT's message limits, Canva's AI credit system, many AI photo editing apps.

**Hybrid with subscriptions**: The most common pattern is a subscription that includes a monthly credit allotment, with the option to purchase additional credits as consumables. This gives you baseline recurring revenue plus upside from heavy users.

---

## 8. Financial Independence Math

The power of the minimalist entrepreneur approach is that you don't need millions of users. You need enough paying customers to sustain yourself.

### The Core Calculation

- **Monthly income needed**: What do you need per month to cover your living expenses and business costs?
- **Revenue per customer**: Your price minus Apple's cut minus any per-user costs.
- **Customers needed**: Monthly income / Revenue per customer.
- **Time to reach that number**: At a realistic acquisition rate, how long does it take?

### Worked Scenarios

**Scenario A: Simple Utility App**
- Price: $2.99/month ($2.54 after Apple's 15% cut)
- Monthly income target: $3,000
- Customers needed: 1,181 active subscribers
- At 2 new subscribers/day with 5% monthly churn: ~18 months to reach target
- Reality check: This is a grind. Low price means you need volume.

**Scenario B: Productivity App**
- Price: $9.99/month ($8.49 after Apple's cut)
- Monthly income target: $5,000
- Customers needed: 589 active subscribers
- At 2 new subscribers/day with 4% monthly churn: ~12 months to reach target
- Reality check: Very achievable for a well-positioned app in a clear niche.

**Scenario C: Professional Tool**
- Price: $19.99/month ($16.99 after Apple's cut)
- Monthly income target: $8,000
- Customers needed: 471 active subscribers
- At 1.5 new subscribers/day with 3% monthly churn: ~14 months to reach target
- Reality check: Fewer customers needed, but each one expects more. Support costs are higher, feature expectations are greater.

**Scenario D: Annual-First Pricing**
- Price: $49.99/year ($42.49 after Apple's cut) = $3.54/month effective
- Monthly income target: $5,000
- Annual subscribers needed: ~1,412 (assuming even distribution of renewals)
- Advantage: Much lower churn on annual plans (typically 50-70% annual retention vs 70-85% monthly). Cash flow is lumpy but more predictable.

### Churn Matters More Than Acquisition

A critical insight most indie developers miss: reducing churn by 1% has a larger long-term impact than increasing acquisition by 10%. If you have 500 subscribers and 5% monthly churn, you lose 25 customers/month. Dropping churn to 4% means losing 20 -- you've effectively "acquired" 5 customers for free, every month, compounding forever.

---

## 9. Tiered Pricing Design

### When to Introduce Tiers

- After you understand your customer segments (typically after 50-100 paying customers)
- When you notice distinct user groups with different willingness to pay
- When you have features that naturally differentiate (individual vs team, basic vs power user)
- When your conversion data shows you're leaving money on the table at a single price point

### The Three-Tier Framework

Three tiers is the sweet spot. Fewer than three and you can't anchor effectively. More than three and you create decision paralysis.

**Free/Basic Tier**: The acquisition funnel.
- Include enough functionality to reach the "aha moment"
- Limit by usage, not by crippling core features (e.g., limit to 3 projects, not "export is disabled")
- Goal: convert to paid, not sustain free users indefinitely
- Examples: Todoist Free (5 projects, 5 collaborators), Notion Free (single user, limited blocks), Bear Free (no sync, no export)

**Pro/Standard Tier**: Your bread and butter. This is where 60-80% of revenue should come from.
- Remove usage limits
- Add productivity features (themes, widgets, automation, advanced filters)
- Price at the "no-brainer" level for your target user
- Examples: Todoist Pro ($4/month, 300 projects, reminders, comments), Bear Pro ($2.99/month, sync, export, themes), Notion Plus ($10/month, unlimited blocks, file uploads)

**Premium/Business Tier**: The high-margin tier for power users and teams.
- Team collaboration, admin controls, priority support
- Advanced features: analytics, API access, integrations, custom branding
- Price at 2-4x the Pro tier
- Examples: Todoist Business ($6/user/month, team features, admin), Notion Business ($18/user/month, SAML SSO, bulk export), Fantastical Premium for Teams

### Worked Example: A Note-Taking App

| | Free | Pro ($4.99/mo) | Team ($9.99/user/mo) |
|---|---|---|---|
| Notes | 50 | Unlimited | Unlimited |
| Sync | No | Yes (all devices) | Yes (all devices) |
| Export | Plain text only | Markdown, PDF, HTML | All formats + bulk |
| Themes | Default only | All themes | All + custom branding |
| Collaboration | None | Share individual notes | Shared workspaces, permissions |
| Support | Community forum | Email (48h response) | Priority (4h response) |
| Storage | 100 MB | 5 GB | 20 GB per user |

### Feature Allocation Principles

- **Never gate core functionality behind the paywall.** The free tier should solve the core problem. Gating core features creates resentment, not upgrades.
- **Gate convenience and scale.** Limits on quantity (projects, notes, storage) and convenience features (sync, export, themes) are the most accepted paywalls.
- **Gate collaboration.** Sharing, teams, and permissions are natural paid features because they correlate with professional use and higher willingness to pay.
- **Gate power-user features.** Automation, API access, integrations, and advanced analytics serve users who derive the most value and will pay the most.

---

## 10. Revenue Optimization Strategies

### Paywall Optimization

Your paywall screen is the highest-leverage design in your app. Small changes yield large revenue differences.

- **Show the value before the price.** Lead with what the user gets, not what it costs. "Unlimited notes, sync across all devices, beautiful themes" above the price, not below.
- **Default to annual.** Pre-select the annual plan. Most users accept the default. This alone can increase annual plan adoption by 20-40%.
- **Show savings explicitly.** "Save 33%" or "2 months free" next to the annual price.
- **Use social proof.** "Trusted by 50,000 writers" or "4.8 stars from 12,000 reviews."
- **Minimize UI friction.** One tap to subscribe. Don't make users navigate multiple screens.

### Trial Optimization

- **Require payment method upfront for the trial.** This dramatically increases conversion (from ~2-5% to ~15-30%) because only serious users start the trial, and many forget to cancel. Apple supports this natively.
- **Send reminders before trial expiration.** This seems counterintuitive, but it builds trust and reduces refund requests. Users who feel respected are more likely to convert.
- **Onboard aggressively during the trial.** Day 1: welcome + setup. Day 3: key feature highlight. Day 5: "Here's what you've accomplished." Day 6: trial ending reminder with upgrade prompt.

### Reducing Churn

- **Grace periods for failed payments.** Apple handles this with billing retry, but communicate proactively ("We noticed an issue with your subscription -- here's how to fix it").
- **Win-back offers.** Use Apple's promotional offers to re-engage lapsed subscribers. A "50% off for 3 months" offer to a churned user is pure profit compared to losing them entirely.
- **Feature announcements.** Regularly communicate new features to subscribers. People cancel when they forget the value. Remind them.
- **Annual plan nudges.** Offer monthly subscribers a discounted switch to annual after 3-4 months. They've proven they value the product; lock in the commitment.

### Price Increases

- **Grandfather existing customers.** Honor their original price for at least 6-12 months, ideally forever. This builds fierce loyalty.
- **Announce increases in advance.** Give 30-60 days notice. Frame it as investment in the product: "To continue building X, Y, and Z features, we're adjusting pricing."
- **Only raise prices for new customers first.** Test market response without risking existing revenue. If new customer acquisition holds steady at the higher price, you've validated the increase.

---

## 11. Concentric Circles Sales Strategy

Skip the launch. Focus on selling. "Viral success" is a myth. Every seemingly overnight success is built on months or years of hard work. Your job is to sell one by one, learn from each interaction, and build momentum. Manual sales account for 99% of early growth. Word of mouth accounts for 99% of later growth.

### Circle 1: Friends and Family (Customers 1-10)

Start here. Yes, it's uncomfortable. Do it anyway.

- Pitch them on being your first customers, not investors. "I built something and I'd love you to be one of my first users" is flattering, not imposing.
- They trust you more than anyone else. If they won't buy, that's a signal worth understanding.
- Ask for honest feedback, not social media posts. You need candor, not cheerleading.
- Kickstarter's data confirms it: support always begins with people you know.

### Circle 2: Your Community (Customers 10-50)

The community you've identified and have been contributing to. These are subject matter experts who understand the problem your app solves.

- **Make a list of everyone** who has written or shared anything about a similar product, tool, or problem space. Blog posts, tweets, forum threads, Reddit comments, YouTube reviews.
- **Contact them all personally.** Walk them through your product. Offer a free extended trial. Do this hundreds of times. There is no shortcut.
- **Ask for candid feedback.** Not App Store reviews (yet). Not social posts. Just honest reactions: "What would make you pay for this? What's missing? What's confusing?"

### Circle 3: Strangers -- Cold Outreach (Customers 50-100)

Cold emails, calls, and messages work. This is how Gumroad grew. Sahil Lavingia personally scoured the web for people who could benefit and emailed them individually, thousands of times.

**Template 1: The Problem-Aware Stranger**
> "Hi [Name], I noticed you posted about [struggling with X / using a workaround for Y]. I built [App Name] specifically to solve this -- it [one-sentence value prop]. Would love to show you a quick demo, or you can try it free for 14 days here: [link]. Either way, happy to share what we've learned from other [community members / professionals in their field]. Cheers, [Your Name]"

**Template 2: The Competitor User**
> "Hi [Name], I saw you reviewed [Competitor App] and mentioned [specific pain point]. I've been building [App Name] and that exact issue was one of the main things I set out to fix. If you're curious, here's a free trial: [link]. No pressure -- I'm also just happy to chat about [topic area]. Best, [Your Name]"

**Template 3: The Content Creator**
> "Hi [Name], I've been following your [blog / channel / newsletter] about [topic] and really enjoyed your piece on [specific post]. I built [App Name] for [target audience] and think it might be interesting to your audience. Would you be open to trying it out? Happy to set you up with a free account. [Your Name]"

**Template 4: The Re-engagement (Churned User)**
> "Hi [Name], I noticed you tried [App Name] a few months ago. Since then we've shipped [2-3 specific improvements]. I'd love to offer you [X months free / 50% off] to give it another look. If there was something specific that didn't work for you last time, I'd genuinely love to hear it -- it helps us build a better product. [Your Name]"

**Key principles for cold outreach:**
- Personalize every message. Reference something specific about the recipient.
- Don't copy-paste. Each email refines your pitch and sharpens your messaging.
- Use each rejection as a learning opportunity. Ask why. Adjust.
- Keep it short. Under 150 words. One clear call to action.
- Follow up once after 3-5 days. After that, move on.

### Sales is Not a Dirty Word

Reframe how you think about selling:
- You're not convincing anyone. You're helping people find a solution to a problem they already have.
- You already have a relationship with your community.
- Turn every failed conversion into an insight -- either you reached the wrong person, or your product needs work. Both are valuable.
- Sales is an education process: your customers get to know you, and you get to know what resonates.

### When to "Launch"

Don't launch until you have 100 paying customers. Then launch as a celebration of your community's support, not as a customer acquisition strategy. Your "launch" is a thank-you to the people who believed early.

---

## 12. Common Pricing Mistakes

### Mistake 1: Pricing Too Low Out of Fear

**The error**: "Nobody will pay $10/month for my app. I'll charge $1.99."
**Why it's wrong**: Low pricing attracts price-sensitive users who churn faster, demand more support, and leave worse reviews. It also signals low quality. A $2/month app is perceived as a toy; a $10/month app is perceived as a tool.
**The fix**: Price based on value delivered, not your comfort level. If the number feels scary, that's often a sign you're in the right range.

### Mistake 2: No Free Tier When You Need One (and Vice Versa)

**The error**: Requiring payment with no trial for a product nobody has heard of. Or offering a generous free tier that satisfies most users.
**Why it's wrong**: Unknown apps need a way for users to experience value before committing. But a free tier that's too generous eliminates upgrade motivation.
**The fix**: Offer a time-limited free trial (7-14 days) with full features, or a feature-limited free tier that creates natural desire for the paid version. Todoist nails this: Free is useful but the 5-project limit pushes serious users to Pro.

### Mistake 3: Only Offering Monthly Billing

**The error**: One price, billed monthly. Take it or leave it.
**Why it's wrong**: You're leaving 30-50% of potential revenue on the table. Annual plans have dramatically lower churn, better lifetime value, and provide upfront cash flow.
**The fix**: Always offer both monthly and annual. Consider adding a lifetime option at 3-5x annual price. Default the UI to annual.

### Mistake 4: Changing Prices Without Communication

**The error**: Silently raising prices and hoping nobody notices.
**Why it's wrong**: Surprise price increases destroy trust and trigger refund requests, negative reviews, and social media backlash.
**The fix**: Announce changes 30-60 days in advance. Grandfather existing subscribers for a period. Frame the increase as investing in the product.

### Mistake 5: Racing to the Bottom on Price

**The error**: "My competitor charges $5/month, so I'll charge $3/month."
**Why it's wrong**: Price wars are unwinnable for indie developers. The lowest-price competitor usually wins on volume (which you can't match) and everyone's margins shrink to nothing.
**The fix**: Compete on value, positioning, and experience -- not price. Charge *more* than competitors and justify it with better design, better support, or a more focused feature set.

### Mistake 6: Ignoring Apple's Commission in Your Math

**The error**: "I charge $9.99/month so I make $9.99/month."
**Why it's wrong**: Apple takes 15-30%. If you're not in the Small Business Program, your $9.99 is actually $6.99. Build this into every financial model.
**The fix**: Always calculate net revenue (after Apple's cut) when doing financial projections. Use $0.85 or $0.70 per dollar as your effective rate.

### Mistake 7: Feature-Gating Core Value

**The error**: The free version of your note-taking app doesn't let users create more than 3 notes.
**Why it's wrong**: If users can't experience the core value, they won't upgrade -- they'll just leave. Overly restrictive free tiers feel hostile and generate 1-star reviews.
**The fix**: Let users experience the core loop fully. Gate convenience (sync, export, themes), scale (storage, project limits), and collaboration -- not the fundamental action your app exists to perform.

---

## 13. When to Revisit Pricing

Pricing is not a "set and forget" decision. Review it quarterly using these signals:

**Raise prices when:**
- You haven't adjusted in 6+ months and your product has improved significantly
- Conversion rate is unusually high (>8-10% of free trial to paid). This often means price is too low.
- Customers never mention price as an objection in cancellation surveys
- You're adding significant new features or capabilities (especially AI features with real costs)
- Competitor pricing has shifted upward
- You're attracting the wrong customer segment (very cheap pricing attracts low-intent users who churn quickly)

**Lower prices or restructure when:**
- Conversion rate is very low (<1-2%) despite strong engagement metrics
- Cancellation surveys consistently cite price as the top reason
- You're losing to a specific competitor on price and can't differentiate on value
- Your market has shifted (e.g., a major free alternative has launched)

**Restructure tiers when:**
- Usage data shows a bimodal distribution (many light users and many heavy users, with little in between)
- Your highest tier accounts for less than 5% of revenue (it's not compelling enough)
- More than 40% of users are on your free tier with no upgrade path visible in their usage patterns
- You're launching a genuinely new category of features (AI, collaboration, API) that warrants its own tier
