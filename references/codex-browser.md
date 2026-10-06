# Codex browser workflow

Use this reference for the Codex browser integration. Read the current tool documentation; the details below are observed behavior, not a replacement for its supported API.

## Choose and retain the session

- Discover available integrations before reporting a blocker. Prefer a usable verified session; check the built-in browser as a local fallback when it is available. Respect an explicitly named browser and obtain agreement before switching it. Explain once if a switch needs fresh verification. Do not install controllers, change permissions, or use a remote browser to work around an unavailable local connection.
- Reuse the tab binding across turns. Before **every yield**, including a short clarification or status reply, refresh its handoff/deliverable mark when the tool's marks are turn-scoped. Temporary tabs otherwise close automatically. Mark a verified, filled form as a deliverable and leave it open for the user.
- On a stale handle, list tabs in the already-selected browser and rebind the existing portal tab without an automatic full snapshot of filled identity fields. Do not reload an intact form or restart the browser. If the tab really disappeared, restore authorized fields privately in the same browser; check verification and possible email/submission outcomes before repeating any external action.

## Enter identity without an extra supervision loop

- User-directed local prefill is an exception to the default user-entry workflow. For a designated shell configuration, parse only literal assignments for the requested settings; do not evaluate command substitutions, expand shell expressions, or execute the file. Keep values in function-local memory and pass them directly to supported field actions. Tool output should contain only validation booleans or non-sensitive status, never the values or the configuration contents.
- For users who choose `~/.zshrc` prefill, the optional setting names are `PERSONAL_INFO_REAL_NAME`, `PERSONAL_INFO_EMAIL`, `PERSONAL_INFO_PHONE_NUMBER`, `PERSONAL_INFO_ADDRESS`, and `PERSONAL_INFO_NATIONAL_ID`. Recognize literal assignments with or without `export` when that source is authorized. These names are a supported convention, not permission to search identity files or a requirement to configure them. Never embed real values in public examples or fixtures.
- If local prefill is unavailable or incomplete, retain usable authorized fields and hand off only the missing identity fields for direct portal entry. Continue evidence preparation and independent case controls where the portal permits it. A missing `.zshrc` identity setup is not a package failure; visible portal verification remains required before any dependent action. Do not treat local prefill as email verification or declaration acceptance.
- The browser's read-only DOM representation may replace phone/email and other `tel` input values with `<redacted>`. An equality comparison against the real value then fails even after successful entry. Recognize masking first; check displayed counters, field constraints, validation state, and the subsequent verification result. Do not keep retyping, probe for unmasked values, or call the field wrong merely because the inspection API masked it. Distinguish exact verification from checks that only establish length and absence of errors.
- Inspect the verification response through a scoped status element or redacted notice. A visible `驗證成功` is enough to continue. If the user authorized requesting the email, click once and wait for a sent/success/error state before asking for intervention. Do not wait for an assumed `確認` dialog when no such control exists. An ambiguous outcome calls for inspection, not another email request.

### Returning users and first-time email verification

The completed browser run used an identity/email pair that had already been verified; it did not exercise first-time email completion. Public portal code inspected on 2026-10-06 shows two branches:

- Previously verified: the email control receives a prior-verification result, displays a welcome-back message, and unlocks the case form immediately without sending another email. Describe this as prior verification recognized, not a new email successfully sent or clicked.
- Newly requested: the portal displays instructions to follow the email link and checks verification status every 10 seconds using the entered identity/email pair. The email-link page separately updates verification status. This supports expecting the original tab to notice completion even when the link opens elsewhere; it is frontend evidence, not an end-to-end cross-browser test or a guarantee of backend behavior.

For a new user, keep the working tab open and hand off the email link unless separately authorized to follow it privately. Do not request the link/token in chat or save it in logs, fixtures, or screenshots. On return, inspect the working tab for visible success and unlocked case controls. Continue preparation while pending, without creating an indefinite blocking wait. If it stays pending, check the verification page's non-sensitive success/error status with the user, the working tab's connectivity, and any visible recovery control. Do not resend automatically, reload an intact draft, restart the browser, or assume its cookies must be transferred. If a new form becomes necessary, retain the reviewed case and restore it through supported controls once verification is visibly accepted; re-check attachments before adding them again.

Public source evidence (re-check if the portal changes): [form bundle](https://prsweb.tcpd.gov.tw/js/chunk-b2f5649e.33aff5f1.js), [email verification bundle](https://prsweb.tcpd.gov.tw/js/chunk-2d0b8e51.d1bc52e2.js). Inspecting source is read-only; do not call its verification endpoints directly or use an invented email to test the live service.

## Fill and verify incident controls

- Scope reads to the upload card, incident card, active dropdown, or declaration control. Avoid a whole-page DOM/accessibility snapshot once identity is present. Batch known independent fields, then verify selected values and errors in the relevant section.
- Inspect `readOnly` and live options before filling a selector. A read-only district selector needs a click and an actual option selection. A date/hour/minute/road autocomplete can be filtered, but its result must be selected. Use accessible labels and freshly observed attributes; generated element IDs can change between sessions.
- Read the upload documentation once. Start the file-chooser listener before clicking the upload control, confirm multiple-file support, then attach both byte-identical originals together. Verify count, rows, loaded thumbnails, filename, size, and capture time. Successful attachment rows may represent client-side file preparation; do not claim server receipt without an acknowledgment. Do not re-add files after a timeout without inspecting those rows.

## Avoid identity in screenshots

- Prefer scoped DOM verification; screenshots are not required to prove every input. If a review image is useful, capture only the incident region and establish the API's coordinate space before including it.
- A crop based on `getBoundingClientRect()` is viewport-relative. A document-coordinate crop needs the applicable `scrollX`/`scrollY` offsets, but that arithmetic alone is not proof that a particular screenshot backend uses the same coordinates or scale. In the observed run, the first viewport-relative crop captured the identity card; later document-offset crops still did not align exactly with the intended elements.
- Compare the proposed crop with the identity region's bounds and allow a separation margin. If coordinate/scale semantics cannot be verified, skip the screenshot and use scoped DOM evidence. Scrolling alone is not protection. Never take a full-page screenshot and redact it afterward to satisfy an incident-only capture requirement.
- Inspect a safely scoped result before saving or sharing it. If a crop unexpectedly includes identity, stop captures, do not save or repeat that image, clear transient image buffers, disclose the mistake briefly, and use scoped DOM reads until a safe capture method is established. Do not claim that the original tool output was removed.

## Complete one review

Show plate, local incident time, confirmed full address, selected category, reviewed description, attachment status, and the declaration's substance together. Preserve the user's stop point. An instruction to accept the displayed declaration but not submit is actionable: check it, verify the state, keep `送出` untouched, and leave the tab open. Only request a missing fact, a genuinely needed verification step, or a required action-time confirmation; do not ask the user to supervise ordinary controls.
