# First 10 Discovery Missions

**Status:** Initial research leads for a community pilot, not verified findings of reusable value.  
**Prepared:** 2026-11-09  
**Evidence rule:** Each mission begins with a public source. Contributors must verify the current state and preserve source dates. Do not infer ownership, license permissions, safety, or present-day usefulness from public availability.

## How to work a mission

For every candidate, record:
1. **Identity:** canonical name, maintainer/publisher, stable URL, version or snapshot date.
2. **Provenance:** original source, upstream links, author/publisher, known forks or mirrors.
3. **Current state:** active, archived, discontinued, superseded, unknown; cite the evidence and date.
4. **Potential value:** what capability, knowledge, data, or historical context may still matter today.
5. **Rights:** separate permission to access, copy, modify, redistribute, and use commercially. Quote the actual license/terms; use `UNKNOWN` when absent or ambiguous.
6. **Risks:** security, privacy, personal data, harmful content, dependency, operational, and provenance risks.
7. **Validation:** a small, reversible test only where rights and safety permit.
8. **Independent review:** a second contributor checks the strongest claims and the strongest counterargument.

Use the labels **FACT / INFERENCE / UNVERIFIED / CONFLICT / UNKNOWN**. A mission is complete when its evidence and limitations are documented—not when a positive value claim is produced.

---

## Mission 01 — NASA APOD legacy API: migration and preservation trail

- **Domain:** Software / APIs
- **Starting source:** https://api.nasa.gov/
- **Why investigate:** NASA's API portal states that the legacy APOD API was migrated in September 2026 and is scheduled to be archived on 2026-12-01. This creates a time-bounded case to document what changed, what clients may depend on the old interface, and whether migration guidance or compatibility examples are missing.
- **Research questions:** What endpoints and response fields changed? Which official migration documentation exists? Are there public clients or tutorials still pointing at the legacy endpoint? What can be preserved as documentation without copying restricted material?
- **Deliverable:** a dated migration map, list of affected public references, and a minimal compatibility note based on official documentation.
- **Caution:** Do not call the old API “abandoned” before checking the announced retirement status and exact cutoff. Do not assume all NASA materials share identical rights.

## Mission 02 — Find a high-potential, underused NASA open dataset

- **Domain:** Data / Science
- **Starting source:** https://data.nasa.gov/
- **Why investigate:** NASA describes this portal as a metadata catalog linking to datasets hosted across different archives. A catalog entry is a discovery route, not proof that the underlying data is complete, accessible, or reusable.
- **Research questions:** Select one dataset with a clearly described scientific or public-interest use case. Is the underlying data still reachable? Is the metadata current? Are format, coverage, update cadence, and usage terms clear? Is there a documented user need it could meet?
- **Deliverable:** one dataset evidence card, source-to-hosting trace, metadata quality review, and one realistic reuse hypothesis.
- **Caution:** Verify rights and terms at the actual hosting archive; do not infer them from the catalog page.

## Mission 03 — NASA open-source code catalog: locate a reusable technical component

- **Domain:** Software / Engineering
- **Starting source:** https://code.nasa.gov/ (catalog described at https://www.nasa.gov/nasa-data-by-subject/)
- **Why investigate:** NASA says its code catalog aggregates open-sourced NASA code projects, including projects not necessarily hosted under the NASA GitHub organization.
- **Research questions:** Find one project whose original purpose is still relevant or whose code may have a second use. Confirm the canonical repository, license, last meaningful maintenance signal, dependencies, build/test status, and whether a successor exists.
- **Deliverable:** a project profile and a reproducible, non-invasive build/test assessment where feasible.
- **Caution:** “NASA catalogued” does not mean every third-party dependency or bundled asset has identical licensing.

## Mission 04 — OpenSSF Scorecard: identify maintenance signals without confusing them with value

- **Domain:** Software / Security
- **Starting source:** https://github.com/ossf/scorecard
- **Why investigate:** OpenSSF Scorecard publishes security-health checks and public scan data. Its maintenance guidance explicitly warns that inactivity is a signal for further investigation, not automatic proof that a project is bad; some stable utilities need little maintenance.
- **Research questions:** Select one older project with a concerning or ambiguous maintenance signal. Check whether the signal is meaningful for that project's purpose, whether there are unresolved security issues, and whether a safe maintenance or documentation contribution is possible.
- **Deliverable:** a dated project-health note with raw evidence, limitations, and a human-reviewed recommendation (investigate / preserve / contribute / do not reuse).
- **Caution:** Do not turn a score into a quality ranking or a claim that a maintainer is negligent.

## Mission 05 — Hugging Face dataset card: trace one dataset's provenance and permissions

- **Domain:** AI / Data
- **Starting source:** https://huggingface.co/docs/hub/main/datasets-cards
- **Why investigate:** Dataset cards can document contents, intended use, bias, license, language, and size. The existence of a card does not guarantee the statements are complete or accurate.
- **Research questions:** Choose one dataset card. Trace the dataset to its original source; compare the platform license metadata with upstream terms; inspect version history and known restrictions; identify missing provenance, consent, privacy, or bias information.
- **Deliverable:** a provenance graph and rights-gap report, with each link classified by evidence strength.
- **Caution:** Do not download or redistribute personal/sensitive data. Do not treat a platform license field as conclusive if upstream sources conflict.

## Mission 06 — Data Provenance Explorer / DPCollection: assess a research infrastructure asset

- **Domain:** AI / Research infrastructure
- **Starting source:** https://www.dataprovenance.org/ and the peer-reviewed study https://doi.org/10.1038/s42256-024-00878-8
- **Why investigate:** The published research reports a large-scale audit of dataset licensing and attribution and describes an open-source provenance exploration resource. This is a candidate for assessing whether an existing public-interest tool can be reused, extended, or connected to other workflows.
- **Research questions:** What data and methods are actually available? Can another researcher reproduce a sample of the reported provenance checks? What are the repository's current maintenance and licensing states? What gaps remain for non-expert users?
- **Deliverable:** reproducibility note, tool capability map, and one proposed improvement backed by a user need.
- **Caution:** Treat research findings as bounded by their sample and method; do not generalize percentages to every dataset platform or current corpus.

## Mission 07 — Internet Archive software item: distinguish preservation from reuse rights

- **Domain:** Digital preservation / Software history
- **Starting source:** https://archive.org/details/software
- **Why investigate:** The Internet Archive preserves digital materials, but item-level rights statements and uploader-provided metadata can vary. This is an ideal test of the project's rule that preservation, access, copying, modification, and redistribution are separate questions.
- **Research questions:** Select one software item with a clear historical record. Who uploaded it? Is there an original publisher or author? What rights statement appears on the item? Can provenance be corroborated elsewhere? Is there a lawful, safe way to study it without redistributing it?
- **Deliverable:** a preservation-focused evidence card and a rights uncertainty map.
- **Caution:** Do not assume that availability on an archive grants permission to download, redistribute, emulate, or commercialize. Avoid executing unknown binaries.

## Mission 08 — GitHub repository revival tooling: evaluate a second-life enabler

- **Domain:** Developer tools / Infrastructure
- **Starting source:** https://github.com/openng-org/github-repo-migration
- **Why investigate:** This public project describes a tool for migrating repository history and issue/PR context from archived or inactive GitHub repositories. It may help preserve project context when maintainers and permissions allow.
- **Research questions:** Does the tool work as documented? What data does it migrate or omit? What permissions and token scopes are required? How does it handle secrets, large files, branches, licenses, and source attribution? Is it maintained and safely usable today?
- **Deliverable:** a feature/limitations matrix and a sandbox test using only repositories the tester owns or has permission to copy.
- **Caution:** Do not migrate third-party repositories or issue data without considering licenses, privacy, platform terms, and contributor expectations.

## Mission 09 — NASA Technical Reports Server: connect an older research result to a present need

- **Domain:** Research / Knowledge
- **Starting source:** https://ntrs.nasa.gov/
- **Why investigate:** Technical reports can contain methods, engineering knowledge, and historical problem-solving that may remain useful after the original project ends.
- **Research questions:** Select one older report with a clearly stated technical problem. Has the method been superseded? Are there modern tools or open datasets that make its approach newly testable? What rights and export-control notices apply to the specific report?
- **Deliverable:** a historical-to-current comparison and a small, safe validation proposal.
- **Caution:** Do not assume every report is public domain or unrestricted. Check report-specific notices and relevant legal restrictions.

## Mission 10 — Open government data: discover a neglected dataset with a defined user

- **Domain:** Public data / Civic technology
- **Starting source:** https://www.data.gov/
- **Why investigate:** Data.gov aggregates federal open-data resources. The opportunity is not “collect more data”; it is to find a dataset that is hard to discover or use and match it to a concrete, underserved need.
- **Research questions:** Choose one dataset and name a plausible user group (researchers, local communities, educators, journalists, or service designers). Is the dataset still updated? Is its schema documented? Are there known quality gaps? Does an existing tool already solve the same problem?
- **Deliverable:** a user-need statement, dataset quality card, and a small prototype or analysis using only permitted data.
- **Caution:** Check the dataset publisher's terms, privacy content, update history, and limitations. Do not infer that aggregator presence guarantees suitability.

---

## Pilot completion criteria

A mission should not be marked “validated” unless it has:
- a canonical source and dated evidence;
- a clear separation of FACT, INFERENCE, UNVERIFIED, CONFLICT, and UNKNOWN;
- a rights and risk review proportionate to the proposed use;
- a documented counterargument or limitation;
- at least one independent review for consequential claims.

**Success is learning and responsible reuse—not finding ten things to copy.** A well-supported conclusion that an asset should not be reused is a successful research outcome.


## Mission 01 pilot status — 2026-11-09

**Status: REVIEW_REQUIRED.** The first desk-research report is available at [Discovery Report 001 — NASA APOD API Migration & Preservation Trail](reports/001-nasa-apod-api-migration.md).

The research confirmed the announced migration and retirement timeline, identified official replacement feed options, and found conflicting documentation about query parameters and response-field semantics. Live endpoint behavior and independent reproduction remain unverified. Do not treat this mission as technically validated or rights-cleared.
