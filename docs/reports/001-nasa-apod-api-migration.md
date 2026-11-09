# Discovery Report 001 — NASA APOD API Migration & Preservation Trail

**Project:** Internet Reclaimer  
**Mission:** 01 — NASA APOD legacy API migration and preservation trail  
**Checked:** 2026-11-09  
**Skill used:** Internet Reclaimer Skill V0.1 for the initial research; findings informed V0.2  
**Review state:** REVIEW_REQUIRED  
**Research mode:** Public-source desk research. No private systems accessed; no binaries executed; no live API request successfully validated in this research pass.

## 1. Executive summary

NASA's Astronomy Picture of the Day (APOD) service is undergoing a documented API transition. NASA's Open APIs page says the APOD API migrated to a WordPress endpoint on 2026-09-10 and that the legacy `api.nasa.gov/planetary/apod` service will be taken offline on 2026-12-01. NASA identifies the replacement endpoint as:

`https://science.nasa.gov/wp-json/wp/v2/apod-basic`

The NASA `nasa/apod-api` repository says its backend has been rewired to the new WordPress endpoint and describes itself as a pass-through/compatibility service. This suggests that the legacy wrapper may continue to shield existing clients during the transition period, but the public notice still gives a retirement date for the legacy service.

**Important research finding (refined on 2026-11-09):** The apparent parameter conflict is likely explained by two interface layers. NASA's Open APIs page and the `nasa/apod-api` compatibility wrapper describe the legacy-compatible parameter set (`date`, `start_date`, `end_date`, `count`). The APOD Feed and API User Guide describes the underlying WordPress endpoint's native filters (`page`, `per_page`, `date_from`, `date_to`) and date-coded item route. The wrapper source code shows it translating legacy `start_date`/`end_date` values into `date_from`/`date_to` before calling the WordPress endpoint. This is strong source-code evidence of an adapter layer, not proof that every documented route works as described at runtime. A controlled request test is still required.

This is not evidence of an abandoned or ownerless asset. The strongest potential value is preserving a reliable migration trail, clarifying interface differences, and helping downstream developers avoid broken integrations.

## 2. Identity and provenance

- **Service:** Astronomy Picture of the Day (APOD) API.
- **Legacy gateway:** `https://api.nasa.gov/planetary/apod` (legacy service path; versioned route described in the repository).
- **Replacement endpoint:** `https://science.nasa.gov/wp-json/wp/v2/apod-basic`.
- **Official API catalog:** https://api.nasa.gov/
- **Service source repository:** https://github.com/nasa/apod-api
- **New feed/API guide:** https://api.nasa.gov/assets/files/apod/APOD-APIs-and-RSS-info.pdf
- **APOD rights explanation:** https://science.nasa.gov/apod/apod-about/
- **NASA media guidance:** https://www.nasa.gov/nasa-brand-center/images-and-media/

NASA's API catalog states the migration date and retirement date. The service repository records a final update dated 2026-09-10 and describes the backend change. The PDF guide documents the WordPress APOD Basic JSON, HTML, RSS, and future-APOD feeds.

## 3. Evidence register

### FACT

**F1 — Migration and retirement dates.** NASA's Open APIs page says the APOD API migrated to the new WordPress API on 2026-09-10 and that the legacy API will be taken offline on 2026-12-01.  
Source: https://api.nasa.gov/ (APOD section)

**F2 — Replacement endpoint.** NASA identifies `GET https://science.nasa.gov/wp-json/wp/v2/apod-basic` as the new endpoint.  
Source: https://api.nasa.gov/

**F3 — Repository transition statement.** The `nasa/apod-api` README says the backend was rewired to the WordPress endpoint, describes the service as passing calls to the new endpoint, and says the repository will be archived/pointed to the new endpoint on 2026-12-01.  
Source: https://github.com/nasa/apod-api

**F4 — New feed options.** NASA's APOD Feed and API User Guide documents:
- APOD Basic JSON list endpoint;
- pagination using `page` and `per_page` (maximum 25);
- date ranges using `date_from` and `date_to` in legacy `YYMMDD` format;
- one item by `/apod-basic/{YYMMDD}`;
- a raw HTML route;
- APOD Basic RSS and year/month filters;
- a separate future-APOD JSON endpoint.  
Source: https://api.nasa.gov/assets/files/apod/APOD-APIs-and-RSS-info.pdf

**F5 — Rights are item-specific.** APOD says images are credited to their owners/institutions; some are copyrighted and require permission from the copyright holder for public or commercial use. NASA/APOD cannot grant permission for those third-party images.  
Source: https://science.nasa.gov/apod/apod-about/

**F6 — NASA media is not a blanket permission for every APOD item.** NASA says its own content is generally not subject to U.S. copyright, but third-party copyrighted material may appear on NASA sites; NASA's permission does not convey rights to others. NASA identifiers and implied endorsement are also restricted.  
Source: https://www.nasa.gov/nasa-brand-center/images-and-media/

### INFERENCE

**I1 — The migration has preservation value.** A dated compatibility/migration guide could help maintainers of small apps, educational projects, archives, and feed readers understand which interface to use and what data fields to expect.

**I2 — The highest-value contribution may be documenting interface layers, not code recovery.** The official materials describe a legacy-compatible gateway and a native WordPress API. The compatibility source code appears to translate between their parameter conventions.

**I3 — The old wrapper may provide a temporary compatibility layer.** The repository says it forwards calls to the new endpoint. This should not be interpreted as a guarantee that every old client behavior or response field is preserved after the retirement date.

### CONFLICT / INTERFACE-LAYER RECONCILIATION

**C1 — Parameter differences are likely explained by two interface layers (runtime pending).**
- NASA Open APIs page describes the legacy-compatible gateway parameters: `date` (YYYY-MM-DD), `start_date`, `end_date`, and `count`.
- The APOD Feed and API User Guide describes native WordPress endpoint filters: `page`, `per_page`, `date_from`, `date_to` (YYMMDD), and a date-coded path.
- NASA's `nasa/apod-api` wrapper source shows its code converting legacy `start_date`/`end_date` values into `date_from`/`date_to` before requesting the WordPress endpoint.

**Refined assessment:** these sources are likely describing different layers rather than contradictory specifications. This explanation is supported by source inspection, but exact live behavior, route availability, and edge cases remain unverified. Keep runtime validation open.

**C2 — Response-field semantics need careful mapping.** The feed guide describes `url` as the APOD post URL, matching `permalink`; the indexed wrapper implementation assigns `url` from `hdurl` in its response transformation. This suggests the wrapper may preserve a legacy client expectation while the native endpoint uses a different meaning. Verify against current source and actual responses before publishing a field mapping.

## 4. Condition and technical state

- The official service repository is public and provides source code, tests, a Docker setup, and an Apache-2.0 license for the repository code.
- The README describes a 2026-01-21 code refresh and a 2026-09-10 backend rewiring.
- NASA's API catalog still carries the retirement notice and points to the WordPress endpoint.
- The new feed guide documents multiple consumption modes (JSON, raw HTML, RSS, future posts), suggesting the replacement is not merely a one-for-one URL substitution.

**Not tested in this pass:** live HTTP status, rate limits, exact response shape for current and historical dates, date-range pagination behavior, error handling, and parity between legacy and new responses. The web reader could not retrieve the live JSON endpoint directly. No claim of runtime verification is made.

## 5. Potential value and users

| Value dimension | Assessment | Rationale |
|---|---|---|
| Historical | Medium | A documented transition in a long-running public astronomy resource. |
| Technical | Medium–High | A useful real-world case of API compatibility, endpoint migration, schema mapping, and feed alternatives. |
| Educational | High | Clear learning case for API lifecycle management and source/rights distinctions. |
| Practical | Medium | A concise migration matrix could reduce integration confusion for downstream users. |
| Economic | Unverified / not the purpose | No evidence of a commercial opportunity or demand was established. |

**Potential beneficiaries:** maintainers of APOD clients, educators, hobbyist astronomers, archive operators, public-data integrators, and developers maintaining older examples/tutorials.

## 6. Rights and access review

| Permission dimension | Current evidence | State |
|---|---|---|
| Read public API documentation | Public NASA pages and guide | FACT |
| Access public API endpoints | Public endpoint documented; live behavior not tested here | UNVERIFIED |
| Copy/modify repository code | Repository displays Apache-2.0 license | FACT, limited to repository code and covered files |
| Redistribute repository code | Subject to Apache-2.0 terms and notices | FACT, limited to covered code |
| Reuse APOD text/images | Item-specific credits and third-party rights apply | REVIEW_REQUIRED |
| Commercial use of APOD media | NASA guidance plus individual third-party rights and publicity/endorsement limits | REVIEW_REQUIRED |

Do not treat the repository's Apache-2.0 code license as a license for APOD images, explanations, or other content. For every media item, inspect the credit line and source owner's terms. NASA's general media guidance does not override third-party rights.

## 7. Safety and ethical concerns

- Do not bulk-copy APOD media merely because it is accessible through an API.
- Do not remove or obscure credit and copyright information.
- Do not imply NASA endorsement.
- Do not treat all APOD items as public domain.
- Do not build a mirror or dataset until item-level rights and terms have been assessed.
- Do not publish personal contact details beyond official organizational contact channels already intended for public use.

No security vulnerability or malicious behavior was investigated or claimed in this mission.

## 8. Reuse and preservation pathways

1. Publish a migration comparison table showing legacy wrapper, replacement JSON, raw HTML, and RSS options.
2. Add a small test matrix for one current date, one historical date, a short date range, pagination, and a missing/invalid date.
3. Compare field semantics, especially `url`, `hdurl`, `permalink`, `media_type`, and `basic_html_url`.
4. Clearly label any undocumented or inconsistent behavior as unresolved.
5. Preserve links, documentation versions, and checked dates rather than copying third-party images.
6. If appropriate, submit a narrowly scoped documentation clarification to the relevant maintainers after tests establish the exact discrepancy.

## 9. What remains unknown

- Whether the replacement endpoint currently accepts the portal's `date`, `start_date`, `end_date`, and `count` parameters exactly as described.
- Whether the PDF guide's `date_from`/`date_to` and pagination behavior is current for the same endpoint version.
- Whether the legacy gateway preserves every historical response field and error behavior until 2026-12-01.
- Whether clients using the old gateway need code changes before retirement or only a base-URL change.
- Whether any downstream projects are currently dependent on the legacy endpoint at meaningful scale.
- Exact rate limits and service-level expectations for the replacement endpoint.

## 10. Recommended next action

**Do not mark this mission ACCEPTED yet.** Keep it at **REVIEW_REQUIRED**.

A follow-up source review on 2026-11-09 found that NASA's wrapper source translates legacy date-range parameters to the native WordPress filters. This narrows the documentation question but does not close runtime validation. Direct endpoint URLs could not be retrieved by the available web reader in this pass, so no HTTP status or live response schema is claimed.\n\nThe next validation step is a controlled, read-only comparison of:
- legacy endpoint, while still available;
- replacement JSON endpoint for a current APOD date;
- replacement JSON endpoint for a historical APOD date;
- replacement date-range and pagination requests;
- one RSS item and one raw HTML route.

Record request URL, response status, response schema, checked time, and any differences. Do not download or republish image files. If a direct runtime test cannot be performed, ask a volunteer with a safe HTTP client to run the documented test matrix and attach sanitized outputs.

## 11. Skill evaluation — V0.1

**What worked**
- The Skill led to canonical-source-first research.\n- Cross-reading the compatibility wrapper source helped distinguish legacy gateway parameters from native WordPress filters, reducing a false-positive documentation-conflict claim.
- It prompted a rights review separate from technical value.
- It preserved uncertainty and supported a negative/qualified outcome rather than forcing a “hidden treasure” claim.
- Its structured output template made the findings and unknowns visible.

**Gaps exposed**
- The Skill should require interface-layer mapping before labeling documentation differences as unresolved conflicts.
- It needs an explicit distinction between source-code license and licenses/rights for content returned by the software.
- It needs a hard rule distinguishing desk research from live endpoint testing.
- It needs field-semantic comparison as part of API migration investigations.
- It should define REVIEW_REQUIRED as the appropriate state when key behavior or rights remain unresolved.

**Outcome:** V0.1 is useful as a research scaffold, but this mission exposes concrete improvements for V0.2. This report is a desk-research result, not an independent technical verification.
