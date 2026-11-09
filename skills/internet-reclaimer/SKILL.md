# Internet Reclaimer Skill

**Purpose:** Help a person and their AI assistant discover, investigate, and assess potentially overlooked digital value using a transparent, evidence-led, rights-aware workflow.

**Version:** 0.2 pilot revision (2026-11-09).

This is an evolving community draft. It is not a legal opinion, ownership determination, investment recommendation, security audit, or authorization to access or reuse third-party material.

## When to use

Use this Skill when someone:
- finds an old, obscure, abandoned, overlooked, or underused digital resource;
- wants to search for resources that may solve a present-day problem;
- wants to understand whether a digital asset has historical, technical, scientific, cultural, educational, or practical value;
- wants to help the Internet Reclaimer community investigate a lead.

The asset may be software, AI-related, blockchain-related, a product, research, data, creative work, or something not yet classified.

## Core principles

1. Do not assume that old, abandoned, dormant, or unpopular means worthless.
2. Do not assume that public, archived, or inactive means ownerless or free to reuse.
3. Do not claim ownership or permission from discovery alone.
4. Prefer primary sources and preserve canonical links.
5. Label claims FACT, INFERENCE, UNVERIFIED, CONFLICT, or UNKNOWN.
6. Keep preservation basis, access permission, copying, modification, redistribution, and commercial-use permission separate.
7. Never bypass authentication, paywalls, access controls, rate limits, or platform restrictions.
8. Do not expose credentials, personal data, private keys, confidential information, or leaked materials.
9. Do not execute untrusted code or models outside an authorized, isolated environment.
10. Ask for human expert review when rights, safety, ownership, privacy, or material consequences are uncertain.

## Workflow

### 1. Understand the lead
Ask what was found, where it was found, why it seems interesting, and what the discoverer already knows. Accept incomplete clues. Do not fabricate missing facts.

### 2. Identify the asset
Find its canonical name, creator or publisher where known, original source, asset type, versions, and identifiers. Distinguish similarly named projects.

### 3. Reconstruct provenance and history
Use primary sources such as original repositories, official documentation, archived official pages, release records, papers, patents, or public registries. Record dates and exact links. Explain gaps and conflicting evidence.

### 4. Assess condition
Determine whether the resource is accessible, complete, maintained, documented, reproducible, compatible, or damaged. Do not run unsafe artifacts. State what has and has not been tested.

### 5. Develop value hypotheses
Describe possible historical, technical, scientific, cultural, educational, practical, or economic value. Connect each hypothesis to a real potential user or problem. Explain why the asset may have been overlooked and what has changed since its creation. Do not invent demand.

### 6. Review rights, access, and ethics
Record available evidence about creator, owner, license, terms, privacy, third-party content, and restrictions. Separate each permission type. If unclear, mark UNKNOWN or REVIEW_REQUIRED and do not recommend copying, redistribution, or commercial use.

For blockchain-related leads, analyze only public information and authorized documentation. Dormancy does not mean abandonment. Never attempt unauthorized wallet access, key recovery, asset movement, or ownership claims.

### 7. Identify reuse pathways
Possible outcomes include preserve metadata, document, refer to upstream, request permission, reproduce an experiment under a lawful basis, adapt with permission, contact rights holders, or recommend no reuse. Do not treat monetization as the default outcome.

### 8. Produce a structured report
Use the output template below. Cite primary sources and include the date checked. Separate verified findings from hypotheses and unknowns.

### 9. Prepare a community contribution
Suggest an Issue or Pull Request. Include the canonical source, evidence, value hypothesis, rights uncertainties, safety considerations, and requested expertise. Do not submit private or restricted material.

## Required output template

- **Lead title:**
- **Asset category:** software / ai / blockchain / products / research / data / creative / unknown
- **Canonical source:**
- **Discovery context:**
- **Identity and provenance:**
- **History and condition:**
- **Potential value:** historical / technical / scientific / cultural / educational / practical / economic
- **Who might benefit and why:**
- **Evidence:** FACT / INFERENCE / UNVERIFIED / CONFLICT / UNKNOWN
- **Rights and access:** preservation / access / copy / modify / redistribute / commercial use
- **Safety, privacy, and ethical concerns:**
- **Reuse pathways:**
- **What has not been verified:**
- **Recommended next action:**
- **Review state:** QUEUED / RUNNING / REVIEW_REQUIRED / ACCEPTED / REJECTED / BLOCKED
- **Sources and checked date:**

## Quality rule

A good report may conclude that an asset is valuable, uncertain, historically interesting but not reusable, or not worth further work. A clear negative finding is useful. Never inflate value to make a discovery look exciting.


## Additional validation rules — V0.2

These rules were added after the first NASA APOD migration pilot.

### 1. Reconcile conflicting documentation

When official sources describe different parameters, fields, dates, permissions, or workflows:
1. Link to and summarize each source separately.
2. Record publisher, publication/update date when available, and date checked.
3. Identify whether the sources describe different interface layers, versions, or audiences.
4. Label the discrepancy **CONFLICT** until evidence resolves it.
5. Do not combine incompatible sources into one definitive specification.
6. Prefer a controlled, low-impact test or clarification from the responsible maintainer. Otherwise leave the behavior UNKNOWN.

### 2. Separate code rights from content rights

A repository license applies only to files and contributions covered by that license. It does not automatically license images, datasets, text, models, records, or other content returned by the software or linked from it.

For mixed repositories and APIs, assess separately:
- source code and dependencies;
- API metadata and documentation;
- returned text, images, audio, video, and datasets;
- third-party embedded or linked materials;
- trademarks, personal likeness/publicity, and endorsement restrictions.

Never infer blanket reuse permission from a repository LICENSE file or public API access.

### 3. Distinguish desk research from runtime verification

Every report must state its research mode:
- **Desk research:** public documentation and source inspection only.
- **Runtime tested:** requests or tests actually executed; include date, method, sanitized request/response evidence, and limitations.
- **Independently reproduced:** another reviewer reproduced the relevant test or finding.

Never describe a documented endpoint as “working” or “verified” unless a live test was actually performed. If the research environment cannot access the endpoint, state that explicitly and preserve the test as an open task.

### 4. For API migrations, compare behavior—not just URLs

Where safe and authorized, compare:
- endpoint and HTTP method;
- authentication requirements and rate limits;
- query parameters and date formats;
- response status and error behavior;
- field names, types, nullability, and semantics;
- pagination, ordering, and default behavior;
- media links, redirects, and content type;
- historical records and edge cases.

Do not assume a replacement endpoint is behaviorally equivalent because it serves similar content.

### 5. Use review states conservatively

- **QUEUED:** lead accepted for investigation, not yet researched.
- **RUNNING:** research is in progress.
- **REVIEW_REQUIRED:** a material question, conflict, permission issue, or independent check remains open.
- **ACCEPTED:** the evidence package meets the project's stated review criteria; this does not mean the asset is legally cleared or recommended for reuse.
- **REJECTED:** the lead is out of scope, unsupported, or not worth further investigation, with reasons recorded.
- **BLOCKED:** work cannot proceed safely or lawfully without authorization or expert review.

A report based only on desk research should not claim independent technical verification. A conflict in a key interface specification normally requires REVIEW_REQUIRED.
