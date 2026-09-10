# PowMCP Skills

Agent Skills for recurring jobs whose evidence step is a hosted PowMCP check. Each skill teaches the whole job: what to gather, which check to run, how to read the result, what it does not prove, and how to hand off. The procedure stands on its own; the PowMCP tool is the verified-evidence step inside it.

## Install

```bash
npx skills add powmcp/skills
npx skills add powmcp/skills --skill <skill-name>
```

Works with Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, OpenClaw, and every client the skills CLI supports. Claude Code users can also add this repository as a plugin marketplace:

```bash
/plugin marketplace add powmcp/skills
```

## Skills

| Skill | Use when | PowMCP checks |
|---|---|---|
| [`attach-regulator-ready-bom-to-release`](skills/attach-regulator-ready-bom-to-release/SKILL.md) | Attaches the exact CycloneDX or SPDX SBOM to a software release. Use when a release build is prepared for delivery; an SBOM must be valid, conformant, or ready to deliver; document conformance, PURL syntax, SPDX license identifiers, required fields, detected format, or specification version must be assessed; an EU-market release must apply the BSI TR-03183-2 floor of CycloneDX 1.6 or newer or SPDX 3.0.1 or newer; or two distinct release SBOMs need conformance-drift, finding-drift, component-change, or license-change evidence. Not for generating the SBOM from the release build. | [SBOM Check](https://powmcp.com/apps/sbom-preflight/) |
| [`diagnose-rejected-invoice-before-resubmission`](skills/diagnose-rejected-invoice-before-resubmission/SKILL.md) | Diagnoses a rejected e-invoice by reproducing and explaining current EN 16931, Peppol, or bundled CIUS conformance findings before resubmission. Use when a buyer or tax-authority platform rejects an invoice with a business-rule code, an ERP-generated UBL or CII is bounced, or staff ask what must be fixed before retransmission. Not for comparing two unrejected drafts. | [E-Invoice Check](https://powmcp.com/apps/einvoice-check/) |
| [`gate-published-release-before-announcement`](skills/gate-published-release-before-announcement/SKILL.md) | Gates an exact published npm release before its announcement. Use when a package version becomes public, the registry version is live but the announcement is paused, or a maintainer asks to verify what consumers actually receive. Not for pre-publish exports or TypeScript resolution validation. | [npm Package Check](https://powmcp.com/apps/npm-package-preflight/) |
| [`preflight-caption-track-before-client-handoff`](skills/preflight-caption-track-before-client-handoff/SKILL.md) | Preflights each caption track against the destination delivery profile before client handoff. Use when a WebVTT (.vtt), SRT (.srt), or TTML/IMSC (.ttml or .xml) track is frozen for delivery, a client asks whether it is valid, conformant, clean, or ready to deliver, a platform gate needs reading-speed evidence, or the user says before handoff, ready for delivery, or check 20 CPS or 17 CPS. Not for generating, translating, or burning captions into video. | [Caption File Check](https://powmcp.com/apps/caption-file-check/) |
| [`preflight-client-endpoint-before-integration`](skills/preflight-client-endpoint-before-integration/SKILL.md) | Verifies a client’s newly supplied public FHIR endpoint’s declared conformance surface before integration work begins. Use when a client gives a public FHIR base URL or metadata URL and asks what the named server declares, whether its metadata is valid, whether US Core resource types or SMART discovery fields are present, why authorization endpoints cannot be discovered, or whether the endpoint is in good shape before onboarding. Not for validating an individual FHIR resource against its declared profile. | [FHIR Server Check](https://powmcp.com/apps/fhir-server-check/) |
| [`preflight-retailer-bound-epub`](skills/preflight-retailer-bound-epub/SKILL.md) | Preflights the exact retailer-bound .epub build for automated EPUB 2/3 specification failures. Use when a title or revised edition is ready for retailer upload, a store rejected the file, EPUBCheck must run before handoff, or a re-export needs a regression check. Not for accessibility, WCAG, or accessibility-metadata review. | [Ebook File Check](https://powmcp.com/apps/epub-check/) |
| [`produce-client-site-handoff-report`](skills/produce-client-site-handoff-report/SKILL.md) | Produces a client site handoff report with live link-integrity evidence. Use when a client site reaches its launch or major-relaunch gate, before client handoff, after deployment, when a lead needs observed link evidence for sign-off, or when confirmed link failures must be fixed, redeployed, and rechecked before handoff. Not for assessing a client site's WCAG accessibility compliance. | [Broken Link Check](https://powmcp.com/apps/broken-link-check/) |
| [`publish-service-change-feed`](skills/publish-service-change-feed/SKILL.md) | Publishes a validated GTFS Schedule update before the old calendar expires. Use when a service change, calendar rollover, stop rename, or route rename requires a new schedule export; when a public GTFS Schedule ZIP needs a Canonical GTFS Validator check for validity, specification problems, or a consumer publish gate; when exactly two public feeds for the same agency need a regression check; or when a static GTFS feed URL must be submitted for US fixed-route NTD reporting. Not for GTFS-Realtime feeds or feed-portal pages, route planning, live vehicle or arrival questions, automated judgments about whether a timetable reflects real service, predictions of a particular consumer's additional acceptance rules, or comparisons between agencies. | [GTFS Feed Check](https://powmcp.com/apps/gtfs-feed-check/) |
| [`publish-weekly-episode-without-feed-breakage`](skills/publish-weekly-episode-without-feed-breakage/SKILL.md) | Keeps this week's podcast episode from breaking distribution. Use when a new episode is published, before directories pull the revised public RSS feed, when a show is not ready, valid, or healthy, when submission failed, when required metadata, artwork, an enclosure, download, seeking, byte-range delivery, codec, duration, or container behavior is in question, or when comparing two public podcast RSS feeds before a hosting migration or as before-and-after evidence. Not for measuring an episode audio master's LUFS loudness, true peak, clipping, or release-wide consistency. | [Podcast Feed Check](https://powmcp.com/apps/podcast-feed-check/) |
| [`substantiate-eu-ebook-accessibility-claim`](skills/substantiate-eu-ebook-accessibility-claim/SKILL.md) | Substantiates an EU ebook accessibility claim for the release EPUB before approval. Use when a new title or revised edition is prepared for EU sale, during backlist remediation, when someone asks whether an ebook is accessible, whether it will meet EPUB Accessibility 1.1 or the EAA, what WCAG problems it has, or what changed between two proposed builds. Not for checking structural EPUB validity. | [Ebook Accessibility Check](https://powmcp.com/apps/epub-accessibility-check/) |
| [`verify-payment-page-header-change-after-deploy`](skills/verify-payment-page-header-change-after-deploy/SKILL.md) | Verifies deployed payment-page HTTP security headers and produces dated evidence for authorization review. Use when a payment page or its delivery infrastructure changed, after deploy, for PCI DSS v4.0.1 Requirement 11.6.1 evidence, when a reviewer asks whether live headers changed, or for monitoring at least once every seven days. Not for authoring a Content-Security-Policy or other header configuration. | [Security Headers Check](https://powmcp.com/apps/security-headers-check/) |

## How the checks are metered

Every PowMCP endpoint answers 50 requests per connecting client without an account, then 100 requests per calendar month with a free account at powmcp.com/account. The skills state those facts and nothing more; anything beyond that is a conversation with the website, not with a skill.

## Connect an endpoint by hand

Each skill carries its own connect lines. The general shape:

```bash
claude mcp add --transport http powmcp-<app-id> https://powmcp.com/<app-id>/mcp
codex mcp add powmcp-<app-id> --url https://powmcp.com/<app-id>/mcp
gemini mcp add --transport http powmcp-<app-id> https://powmcp.com/<app-id>/mcp
```

## Provenance

Every skill in this repository passed a deterministic gate, a measured evaluation against a tools-only baseline in real headless agents, and an independent three-seat committee appraisal before publication. Skills carry no scripts and make no network calls of their own.

## Feedback

Open an issue at https://github.com/powmcp/skills/issues with the skill name in the title.
