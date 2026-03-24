---
name: skill-merger
description: "Merge multiple related skills into a single unified superskill. Use when the user wants to combine, consolidate, or merge 2+ skills covering the same subject into one comprehensive skill. Triggers: 'merge these skills', 'combine skills', 'create a superskill', 'consolidate skills', 'unify these skills into one'."
---

# Skill Merger

Combine multiple related skills into a single, coherent superskill that preserves the best of each source while staying lean and well-organized.

## Workflow

1. Collect source skills
2. Analyze and classify content
3. Design the merged structure
4. Build the superskill
5. Validate and package

## Step 1: Collect Source Skills

Gather all source skills the user wants to merge. For each skill, read:
- `SKILL.md` (frontmatter + body)
- All files in `references/`, `scripts/`, `assets/`

Ask the user if unclear:
- "Which skills should I merge?"
- "Are there priority skills whose approach should take precedence?"

## Step 2: Analyze and Classify Content

For detailed classification criteria, see [references/merge-methodology.md](references/merge-methodology.md) — sections 1-2.

For each source skill, extract and sort content into three tiers:

**Tier 1 → SKILL.md body**: Workflow steps, decision logic, critical constraints, key examples.
**Tier 2 → references/**: Detailed docs, extended examples, edge cases, background theory.
**Tier 3 → assets/**: Templates, boilerplate, images — files used in output.

### Identify overlaps and conflicts

- Map which skills cover which topics
- Flag contradictions between skills (see [references/merge-methodology.md](references/merge-methodology.md) — section 3)
- Note duplicated content for deduplication (see [references/merge-methodology.md](references/merge-methodology.md) — section 4)

## Step 3: Design the Merged Structure

### Frontmatter description
Synthesize trigger patterns from all source skills into one comprehensive description. Cover every scenario that any source skill handled.

### Body structure
Choose the structure that best fits the combined content:

- **Workflow-based** — When source skills form a sequential pipeline
- **Task-based** — When source skills cover different operations on the same domain
- **Hybrid** — Main workflow with task-specific branches

### Reference file plan
Organize reference files by topic, not by source skill:

```
references/
├── api-reference.md      (combined API docs from all sources)
├── advanced-patterns.md   (edge cases and advanced usage)
└── examples.md            (comprehensive example collection)
```

See [references/merge-methodology.md](references/merge-methodology.md) — section 5 for naming conventions and organization guidelines.

## Step 4: Build the Superskill

### Write SKILL.md
1. Write the merged frontmatter with unified name and comprehensive description
2. Write the body with the designed structure:
   - Synthesize workflows into a coherent flow — don't just concatenate
   - Keep only Tier 1 content in the body
   - Link to reference files with clear "when to read" guidance
3. Stay under 500 lines

### Create reference files
- Organize Tier 2 content by topic
- Add table of contents to files >100 lines
- Ensure no duplication between SKILL.md and reference files

### Consolidate scripts and assets
- Deduplicate scripts with overlapping functionality
- Test retained scripts
- Organize assets without redundancy

## Step 5: Validate and Package

Run the quality checklist from [references/merge-methodology.md](references/merge-methodology.md) — section 6.

Key checks:
- SKILL.md under 500 lines
- No content duplication across files
- All references linked from SKILL.md
- All trigger scenarios covered in description
- Coherent end-to-end workflow
- Conflicts resolved or flagged to user

Package using `package_skill.py` when ready.
