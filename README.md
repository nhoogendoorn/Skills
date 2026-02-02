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

**Use When:** You need to define design direction for an Apple platform app, create a stable reference that prevents design drift across multiple LLM sessions, or align future design decisions to a single source of truth.

## Usage

Each skill is self-contained with its own documentation. Refer to the `SKILL.md` file in each skill's directory for detailed workflows, guidelines, and examples. Supporting materials like output templates live in the skill's `references/` folder.

## Contributing

Skills are designed to be focused and reusable. When adding new skills, ensure they:

- Have a clear, single purpose
- Include a `SKILL.md` with YAML frontmatter (`name`, `description`) and a complete workflow
- Follow consistent patterns with existing skills
- Include reference materials in a `references/` folder when applicable
