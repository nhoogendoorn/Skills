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

## Usage

Each skill is self-contained with its own documentation. Refer to the `SKILL.md` file in each skill's directory for detailed workflows, guidelines, and examples. Supporting materials like output templates live in the skill's `references/` folder.

## Contributing

Skills are designed to be focused and reusable. When adding new skills, ensure they:

- Have a clear, single purpose
- Include a `SKILL.md` with YAML frontmatter (`name`, `description`) and a complete workflow
- Follow consistent patterns with existing skills
- Include reference materials in a `references/` folder when applicable
