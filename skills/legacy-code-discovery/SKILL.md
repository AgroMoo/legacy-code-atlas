# Legacy Code Discovery Skill

## Purpose
Find potentially reusable historical software and produce an evidence-led candidate assessment. This skill discovers and organizes; it does not certify legal rights or execute untrusted code.

## Workflow
1. Search for candidates using primary sources (original Git repositories, official project archives, release pages).
2. Confirm canonical identity and ownership attribution where available.
3. Capture repository URL, archive status, last activity, release history, language, and dependencies.
4. Explain the original purpose and historical context.
5. Identify a concrete present-day problem the project might help solve.
6. Review license evidence. Separate preservation basis from redistribution right. If uncertain, set UNKNOWN and do not redistribute.
7. Flag security, dependency, build, and runtime risks. Never run code outside an isolated, disposable environment.
8. Produce a concise asset card with evidence labels, citations, checked date, uncertainty, and next actions.
9. Recommend independent human review before public promotion.

## Output format
- Candidate identity and canonical URL
- FACT / INFERENCE / UNVERIFIED / CONFLICT / UNKNOWN claims
- Historical context
- Potential modern use case
- License and rights status (with evidence)
- Safety and compatibility risks
- Review state: QUEUED / RUNNING / REVIEW_REQUIRED / ACCEPTED / REJECTED / BLOCKED
- Next action

## Prohibited
- Claiming a project is abandoned solely because it is archived.
- Treating a public URL as permission to copy or redistribute.
- Claiming compatibility without testing.
- Executing untrusted code on a host or production system.
- Inventing dates, owners, licenses, popularity, or user outcomes.
