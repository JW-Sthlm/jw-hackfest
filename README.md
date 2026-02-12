# Enterprise AI Release Scouting Agent

**Track:** Agents League / TechConnect – Track 2 (Reasoning Agents)  
**Focus:** Reasoning, verification, and trust over automation volume

## Overview

The **Enterprise AI Release Scouting Agent** helps enterprise architects and partners stay current on Microsoft AI platform updates without marketing noise.

It treats Microsoft Foundry blog posts as **signals of change**, then **verifies every capability** against authoritative **Microsoft Learn** documentation before producing output.

The result is a concise, publish-ready **LinkedIn post** that is factual, verifiable, and relevant for enterprise decision-makers. Any capability **without suitable Microsoft Learn documentation is intentionally excluded**.

## What it solves

Enterprise audiences are overloaded by AI announcements across blogs and social channels.

This agent reduces noise by:
- avoiding announcement-only links
- excluding features without enterprise-ready documentation
- focusing on what matters for architects and partners

## How it works

**Core principle:** Blog = signal. Learn = source of truth.

Reasoning workflow:
1. **Detect** – Identify new or updated capabilities from recent Microsoft Foundry blog posts.
2. **Verify** – Search and retrieve authoritative documentation using the Microsoft Learn MCP Server.
3. **Evaluate** – Assess relevance for enterprise architects and partners.
4. **Filter** – Exclude any capability without suitable Microsoft Learn documentation.
5. **Publish** – Generate a concise LinkedIn post with Microsoft Learn links only.

## Architecture

- **Runtime:** Microsoft Foundry Agent Service
- **Model:** `gpt-5.2-chat`
- **Grounding:** Microsoft Learn MCP Server
- **Outputs:**
  - LinkedIn post text (ready to publish)
  - Microsoft Learn links with short descriptions
  - Optional AI image prompt (text only)

### Model choice

`gpt-5.2-chat` is used for strong reasoning and predictable enterprise output.

This model does not support temperature-based sampling controls. Consistency is achieved through:
- strict prompt constraints
- explicit reasoning steps
- authoritative grounding through Microsoft Learn

## Output format

Each run produces:
- **Headline** – Clear factual hook
- **Narrative** – Short paragraphs explaining enterprise relevance
- **Learn more** – 2–3 Microsoft Learn links with short descriptions
- **Optional** – AI image prompt (text only)

### Hard constraints

- No speculation or inferred features
- No marketing language
- No links outside Microsoft Learn
- No blog links in final output

## Example output (excerpt)

```text
Headline: New capabilities for building governed AI agents in Microsoft Foundry

Microsoft Foundry continues to evolve its agent platform with improvements focused on reliability, governance, and enterprise readiness.

These updates matter for architects designing agentic systems that must scale securely across teams and tenants.

Learn more:
- Microsoft Foundry Agent Service overview – Architecture and core concepts
- Model Context Protocol (MCP) – Grounding agents with authoritative documentation
