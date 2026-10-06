# Traffic Reporting Agent Skills

Agent instructions for preparing traffic-violation reports from original photos, videos, or a Road Report case ZIP, then completing an authorized browser workflow on the police reporting portal.

> **Still in testing. Currently supports Taipei City (臺北市) only.**
> New Taipei City (新北市) and other cities/counties are not yet supported. Support for other cities is on the roadmap.

This is an experimental agent skill, not a standalone app or an official police service. Browser compatibility, portal changes, and evidence quality can affect results. Review the facts before authorizing submission. A submitted report does not guarantee police acceptance or a finding of a violation.

## What it does

- Inspects original evidence and available capture-time/GPS metadata.
- Prepares Traditional Chinese report details and identifies missing facts.
- Proposes address details from existing mapped information, clearly marking unverified house numbers.
- Guides an agent through identity/email verification, form entry, attachment checks, and explicitly authorized submission.
- Keeps preparation, uploads, declaration acceptance, and final submission as separate authorization steps.

You can use original media directly; the Road Report frontend and ZIP export are optional. This repository contains instructions, not a bundled browser controller or evidence-processing application.

## Tested environments

User-reported results during testing:

| Setup | Result |
| --- | --- |
| Codex app + built-in browser | Working in tested workflow |
| Dot + Codex app + built-in browser | Working in tested workflow |
| VPS / remote sandboxes | Not usable in tested setups |

Use a local browser for the police-portal workflow. Remote environments encountered portal-access restrictions; these results do not establish that every VPS or remote IP is blocked. Other agent/browser combinations are not yet verified, and these results are not a guarantee for every case or future portal version.

## Get started

Clone this repository on the machine where you will run your agent:

```sh
git clone https://github.com/brian890809/reporting-traffic-agent-skills.git
cd reporting-traffic-agent-skills
```

Ask your agent to read [SKILL.md](SKILL.md). For automatic skill discovery, install `SKILL.md` and the `references/` directory together in a `reporting-taipei-traffic` directory under your agent's supported skill location. Installation and browser capabilities depend on the agent you use.

Start with a preparation-only dry run:

```text
Read SKILL.md and follow the reporting-taipei-traffic skill.
Use the original photos in /absolute/path/to/photos.
Prepare a Taipei City traffic report only. Do not open the police
form, upload files, send verification emails, or submit anything.
Show one concise case review and any missing facts.
```

You can replace the photo path with a video or a Road Report case ZIP. Once the skill is installed, short requests such as `幫我檢舉`, `幫我檢舉違停`, or `檢舉這台車` can select it when the conversation or attached evidence provides traffic-report context. These phrases do not replace case review and submission authorization.

## Try the browser workflow

After reviewing the prepared case:

```text
Fill the Taipei police form and upload the reviewed original files.
Do NOT submit. Prefer your available built-in browser integration;
you do not need to use my existing browser window.
Check portal access, local-file upload support, and whether I can
complete identity/email verification in the same session.
Do not install tools or change permissions.
Verify the fields and attachments, then show one concise final review.
```

The agent needs browser controls that can interact with the [Taipei police portal](https://prsweb.tcpd.gov.tw/), attach local files, and allow you to complete verification. Web search alone is insufficient. Remote browsers may be blocked; a built-in browser is not necessarily local. Codex-specific workflow notes are in [references/codex-browser.md](references/codex-browser.md); availability varies by installation.

## Privacy and limitations

- Keep originals unchanged. Do not commit evidence, identity details, or verification links to this repository.
- Enter identity details directly in the portal by default. Reading an existing local identity source requires explicit authorization; local identity configuration is optional.
- External geocoding requires authorization to send coordinates. GPS identifies the camera's approximate position, not a proven vehicle address.
- Check current reporting eligibility, deadlines, file limits, and portal requirements for each case. Recorded observations in the skill can become outdated.
- The skill references optional helpers from the separate Road Report app; those helpers are not included or required here.

## Roadmap

- Continue testing and improving the Taipei City workflow.
- Add support for other cities and counties, with separate portal mappings, verification flows, and reporting requirements. No release dates are committed yet.

Do not use the Taipei workflow for another jurisdiction until support for that jurisdiction is explicitly documented.

## License

[MIT](LICENSE) — Copyright (c) 2026 Bohan Chen.
