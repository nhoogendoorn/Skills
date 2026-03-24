# Skill Merge Methodology

## Table of Contents

1. Analysis Framework
2. Content Classification
3. Conflict Resolution
4. Deduplication Strategy
5. Reference File Organization
6. Quality Checklist

---

## 1. Analysis Framework

For each input skill, extract and categorize:

| Category | What to look for | Goes into |
|----------|-------------------|-----------|
| Core workflow steps | Sequential procedures, decision trees | SKILL.md body |
| Domain rules | Must-do / never-do constraints | SKILL.md body |
| Trigger patterns | When-to-use descriptions | SKILL.md frontmatter description |
| API/tool docs | Detailed API references, schemas | references/ |
| Code examples | Reusable scripts, utilities | scripts/ |
| Templates/assets | Output templates, boilerplate | assets/ |
| Extended explanations | Background context, rationale, theory | references/ |
| Edge cases & gotchas | Pitfalls and workarounds | references/ (linked from SKILL.md) |

## 2. Content Classification

### Tier 1 — Core (SKILL.md body)
Information that directly enables execution:
- Workflow steps and decision logic
- Critical constraints and guardrails
- Tool/script usage instructions
- Key examples that illustrate non-obvious patterns

### Tier 2 — Reference (references/)
Information that supports execution but isn't needed every time:
- Detailed API documentation
- Comprehensive examples and variations
- Background theory and rationale
- Edge cases and advanced patterns
- Domain-specific schemas or specs

### Tier 3 — Assets (assets/)
Files used in output, not loaded into context:
- Templates, boilerplate
- Images, fonts, icons

## 3. Conflict Resolution

When source skills contain contradictory guidance:

1. **Identify the conflict** — Note exact contradictions (e.g., Skill A says "always use X," Skill B says "never use X")
2. **Check scope** — Often conflicts are context-dependent, not true contradictions (Skill A's rule applies to scenario X, Skill B's to scenario Y)
3. **Prefer specificity** — More specific guidance wins over general guidance
4. **Prefer recent** — If skills were created at different times, newer guidance often reflects learned lessons
5. **Flag unresolvable conflicts** — Present to user with both options and ask for a decision

## 4. Deduplication Strategy

### Concept-level deduplication
When multiple skills explain the same concept:
- Keep the clearest, most concise explanation
- If different skills add unique nuance, synthesize into one explanation
- Never repeat the same information in both SKILL.md and a reference file

### Workflow-level deduplication
When skills share workflow steps:
- Identify the shared "spine" of the workflow
- Factor out shared steps into the main workflow
- Branch into skill-specific steps where they diverge

### Example-level deduplication
When skills provide overlapping examples:
- Keep the most illustrative example for each distinct concept
- Combine complementary examples that show different facets
- Move extensive example sets to references/

## 5. Reference File Organization

### Naming conventions
- Use descriptive, lowercase, hyphenated names: `api-reference.md`, `advanced-patterns.md`
- Group by topic, not by source skill
- Prefix with domain when multiple domains exist: `auth-patterns.md`, `data-patterns.md`

### Structure within reference files
- Start with a table of contents for files >100 lines
- Use consistent heading hierarchy
- Include grep-friendly section headers for large files

### Linking from SKILL.md
Always tell Claude when and why to read a reference file:
```markdown
For advanced caching strategies, see [references/caching.md](references/caching.md).
```

## 6. Quality Checklist

After merging, verify:

- [ ] SKILL.md body stays under 500 lines
- [ ] No duplicated content between SKILL.md and reference files
- [ ] All reference files are linked from SKILL.md with clear "when to read" guidance
- [ ] Frontmatter description covers all trigger scenarios from all source skills
- [ ] Workflow is coherent end-to-end (no orphaned steps from individual skills)
- [ ] Conflicts between source skills are resolved or flagged
- [ ] Scripts from source skills are tested and deduplicated
- [ ] Assets are organized without redundancy
