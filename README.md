```md
# Enterprise AI Release Scouting Agent

## Overview

Enterprise AI Release Scouting Agent helps enterprise architects and partners stay current on Microsoft AI platform updates without marketing noise. The agent treats Microsoft Foundry blog posts as **signals of change**, then grounds every output in **authoritative Microsoft Learn documentation** before publishing.

The result is a concise, publish-ready LinkedIn post that is factual, verifiable, and useful for enterprise decision-makers. Capabilities without authoritative Microsoft Learn documentation are intentionally excluded.

This project was built for **Agents League / TechConnect – Track 2 (Reasoning Agents)**, with a deliberate focus on reasoning, verification, and trust over automation volume.

---

## Problem

Enterprise audiences face an overload of AI announcements across blogs and social channels:

- Marketing posts that link to announcements rather than documentation
- Features shared before enterprise-ready guidance exists
- Difficulty assessing what actually matters for architects and partners

This agent addresses these issues by enforcing a verification-first workflow.

---

## Agent Design

### Core Principle

**Blog = signal. Learn = source of truth.**

Microsoft Foundry blog posts are used only to detect new or updated capabilities. Final outputs always link to Microsoft Learn documentation.

### Reasoning Workflow

1. **Detect** – Identify new or updated capabilities from the latest Microsoft Foundry blog posts  
2. **Verify** – Use the Microsoft Learn MCP Server to search and fetch authoritative Microsoft Learn documentation  
3. **Evaluate** – Assess relevance for enterprise architects and partners  
4. **Filter** – Exclude any capability without suitable Microsoft Learn documentation  
5. **Publish** – Generate a concise, publish-ready LinkedIn post with Microsoft Learn links only  

This workflow demonstrates multi-step reasoning, verification, and intentional exclusion.

---

## Architecture

- **Agent Runtime:** Microsoft Foundry Agent Service  
- **Model:** `gpt-5.2-chat`  
- **Grounding:** Microsoft Learn MCP Server  

**Outputs:**
- LinkedIn post text (ready to publish)
- Microsoft Learn links with short descriptions
- Optional AI image prompt (text only)

### Model Choice Rationale

`gpt-5.2-chat` was selected for its strong reasoning, deterministic behavior, and enterprise alignment. Sampling parameters such as temperature are not supported by this model; consistency is achieved through strict prompt constraints and authoritative grounding.

---

## Output Format

Each run produces:

- **Headline** – Clear, factual hook  
- **Narrative paragraphs** – Why the capability matters for enterprise adoption  
- **Learn more** – 2–3 Microsoft Learn links with short descriptions  
- **Optional** – AI image prompt (text only)

### Constraints Enforced

- No speculation or inferred features  
- No marketing language  
- No links outside Microsoft Learn  
- No blog links in final output  

---

## Example Output (Excerpt)

```text
Headline: New capabilities for building governed AI agents in Microsoft Foundry

Microsoft Foundry continues to evolve its agent platform with improvements focused on reliability, governance, and enterprise readiness.

These updates matter for architects designing agentic systems that must scale securely across teams and tenants.

Learn more:
- Microsoft Foundry Agent Service overview – Architecture and core concepts
- Model Context Protocol (MCP) – Grounding agents with authoritative documentation
