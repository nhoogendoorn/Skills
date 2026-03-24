# Skills

A collection of specialized prompt-based skills for [Claude Code](https://claude.ai/code).

## Overview

This repository contains focused skills designed to assist with design and development workflows. Each skill is a self-contained set of instructions that teaches Claude how to perform a specific task — no code, just structured prompts and reference materials.

## Skills

### 🎨 Swift Design Brief

**Purpose:** Generate a Design Brief for Apple platform apps (iOS, iPadOS, macOS, watchOS) that serves as a long-lived, authoritative reference document for LLM-driven design decisions.

Captures design intent, encodes trade-offs, and provides decision heuristics — not feature lists. The output is structured so another LLM can reliably parse and apply it. Assumes SwiftUI as the primary UI framework and Apple HIG as the baseline.

**Key Features:**
- Generates opinionated, internally consistent design briefs
- Bakes in Apple Human Interface Guidelines as assumed constraints
- Produces decision heuristics that help an LLM say "no" to misaligned choices
- Includes a validation step to catch contradictions before delivery

**Tip:** Provide design inspiration — app names, screenshots, or references — alongside your product description. For example: "I want the information density of Things 3 with the playfulness of Duolingo." Inspiration produces significantly better briefs.

**Use When:** You need to define design direction for an Apple platform app, create a stable reference that prevents design drift across multiple LLM sessions, or align future design decisions to a single source of truth.

### 🖼 SwiftUI Logo Generator

**Purpose:** Generate programmatic SwiftUI logos and app icons from design briefs or user descriptions. Produces self-contained `LogoView` structs using shapes, paths, gradients, and SF Symbols — no external dependencies.

**Key Features:**
- Proposes three distinct logo directions (abstract geometric, lettermark, symbolic icon)
- Generates scalable SwiftUI code that renders at any size from 16pt to 1024pt
- Includes a debug preview sheet for reviewing logos at multiple sizes
- Cross-platform export support (macOS `NSSavePanel`, iOS Photos/ShareLink)
- Apple Icon Composer integration for multi-layer dynamic app icons
- References curated color palettes and shape patterns

**Tip:** Run the Swift Design Brief skill first to generate a design brief — the logo generator uses it to extract color strategy, personality traits, and aesthetic direction for better results.

**Use When:** You want to create an app icon, logo, or branding asset entirely in SwiftUI code — from concept through export to the asset catalog.

### 📱 App Marketing Plan

**Purpose:** Create a comprehensive app marketing strategy by generating four tailored deliverable files: a tone of voice guide, monetization plan (pricing, tiers, paywall strategy), marketing plan (go-to-market, content strategy, ASO, copywriting), and a design brief for marketing visuals.

**Key Features:**
- Single context-gathering phase feeds all 4 deliverables — no repetitive questioning
- Grounded in minimalist entrepreneur philosophy (community-first, spend time before money)
- Includes paywall strategy with trigger points, screen components, and A/B testing roadmap
- Drafts actual App Store metadata respecting platform character limits (Apple & Google)
- Copywriting direction using proven frameworks (PAS, AIDA, StoryBrand)
- Extensive reference guides (4,000+ lines) covering copywriting, paywall patterns, ASO, pricing, and tone of voice
- Minimalist review checkpoint to gut-check the entire plan

**Use When:** You want to plan marketing for a mobile app — from pricing and monetization through content strategy, app store optimization, paywall design, and marketing visuals.

### 📅 100 Days of Marketing

**Purpose:** Generate a 100-day actionable marketing plan for indie macOS or iOS apps. Produces a single markdown file with daily tasks covering content creation, community building, App Store optimization, sales, and paid growth.

**Key Features:**
- Day-by-day marketing tasks across 100 days
- Phased approach: foundation, content, community, optimization, and growth
- Requires input context files (marketing.md, monetization.md, tone-of-voice.md) — pairs naturally with the App Marketing Plan skill

**Use When:** You have your marketing strategy defined and want a concrete day-by-day execution plan to follow.

### 🔀 Skill Merger

**Purpose:** Merge multiple related skills into a single unified superskill. Analyzes source skills, deduplicates content, resolves conflicts, and produces a well-structured merged skill with lean SKILL.md and organized reference files.

**Key Features:**
- Content classification into tiers (core workflow vs. reference material vs. assets)
- Conflict resolution and deduplication across source skills
- Structured merge methodology with quality checklist
- Keeps SKILL.md under 500 lines by offloading detail to reference files

**Use When:** You have 2+ skills covering the same subject and want to consolidate them into a single, coherent skill.

## Usage

Each skill is self-contained with its own documentation. Refer to the `SKILL.md` file in each skill's directory for detailed workflows, guidelines, and examples. Supporting materials like output templates live in the skill's `references/` folder.

## Contributing

Skills are designed to be focused and reusable. When adding new skills, ensure they:

- Have a clear, single purpose
- Include a `SKILL.md` with YAML frontmatter (`name`, `description`) and a complete workflow
- Follow consistent patterns with existing skills
- Include reference materials in a `references/` folder when applicable
