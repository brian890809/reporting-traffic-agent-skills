# New Taipei City traffic reporting

Use this reference only for incidents in 新北市. Shared evidence, authorization, and privacy requirements remain in [SKILL.md](../SKILL.md). These observations come from two completed submissions on 2026-10-12; they establish receipt generation, not police acceptance or eligibility for every case. Re-check current controls, reporting deadlines, categories, and upload limits.

## Entry and declaration

Start at the [official portal](https://tvrs.ntpd.gov.tw/) and follow `交通違規檢舉` to the [declaration page](https://tvrs.ntpd.gov.tw/Home/Report). The observed form route is `/Home/Report_Add`; do not use a direct route to skip the declaration review. Some declaration material is presented as images, so text extraction alone may omit it.

Read the current declaration and summarize its substance in the consolidated case review. The tested declaration covered truthful identity and evidence, necessary police use of personal data, cooperation if clarification is needed, and inability to withdraw after submission. Obtain any missing explicit acceptance before checking it. Carry forward acceptance already given for the reviewed cases; it is distinct from final submission authorization.

## Evidence and form mapping

| Visible control | Source and verification |
| --- | --- |
| Vehicle type / plate type | Actual vehicle and plate class; tested values were `汽車` and `一般車牌` |
| Plate | Two visible segments around the hyphen; verify both |
| Date / hour / minute | Original incident time in Asia/Taipei; observed date displayed Gregorian year |
| City / district / road | Confirmed address; select actual `新北市`, district, then road options |
| Location detail | Supported house number and scene detail; preserve the user's confirmed `附近` wording where appropriate |
| Violation category | Match the current official option to the evidence; tested option was `人行道、行人穿越道違規停車` |
| Description | Concise observable facts and relevant user observations; distinguish parking from temporary stopping or entering/exiting a driveway |
| Attachments | Verify one entry for each reviewed file, with intended filename and successful preparation/upload state |

Use current DOM labels and observed attributes rather than hard-coded IDs. A legacy combined plate input can remain blank while the visible split inputs are filled; do not alter hidden or unused controls to make them look consistent.

The observed form allowed JPG/JPEG/GIF/PNG images; MP4/FLV/MPEG/MKV/MOV/AVI/WMV/TS videos; and ZIP/RAR archives. HEIC was not a directly listed image type. Re-check the live list and size/count limits before upload.

For an original Live Photo, the tested solution attached its original MOV plus a ZIP containing only the matching unmodified HEIC. Verify archive contents and byte equality before uploading. This preserves the original and avoids silently converting it or disguising HEIC as JPEG. Acceptance of the archive by the form does not prove reviewers can use every contained format; resolve any explicit portal incompatibility. Do not upload unrelated photos or a case package containing identity, prompts, or internal notes. A short MOV can show the scene but cannot establish a longer duration by itself.

## Identity and email verification

Use direct user entry or the explicitly authorized private identity source described in the shared workflow. The tested form required name, government ID, contact address, telephone, and email. Never print those values or inspect the full filled page.

- Request `認證信箱` only when authorized. `信件已發送`, including a green check, confirms sending; it does not establish that the link was followed or verification completed.
- Keep the form open while the user follows the email link, unless separately authorized to handle it privately. The observed instructions required verification and report completion within 30 minutes of receiving the email. Re-check the current wording; if verification expires, use the visible recovery flow rather than repeatedly requesting mail.
- Do not impose Taipei's returning-user/polling behavior on this portal. Observe New Taipei's own status and validation.
- In the tested two-case batch, one email verification sufficed for both forms in the same browser session. This is an observation, not a guarantee for another session or email. Do not send a duplicate email merely because a second form lacks a sent marker; respond to an explicit verification requirement or error.

## CAPTCHA and multiple forms

Keep a separate case-to-tab mapping. Prefer completing the current case's CAPTCHA immediately before its authorized submission instead of preparing several codes and assuming they remain valid.

After the browser tool's required action-time confirmation, inspect the actual rendered CAPTCHA in that form. Capture only the image or the image-plus-code input using verified crop coordinates; keep nearby personal fields out of tool output. Use the visible refresh button if unreadable. Re-observe the image after refresh, since an immediate capture can still show the previous challenge. Do not open the image URL in another tab, call a private endpoint, or reuse a code from another form.

During the tested batch, the second form's rendered challenge changed while its input still contained the earlier code. Shared-session invalidation is only a possible explanation, not an established server rule. Compare the current image with the entered code before submission. If they differ before sending, fill the current code within the existing authorization. Do not infer a failed submission solely from a changed CAPTCHA afterward.

## Submit and establish the outcome

1. Verify the reviewed case, attachments, declaration acceptance, email status, and current CAPTCHA. Click `送出` once for that authorized attempt.
2. Inspect scoped validation and active dialogs, then the resulting page. The initial click can return before an alert or receipt appears; an unchanged URL is not failure. A generic alert alone is not proof of rejection or success.
3. The observed success page said `您已經完成流程，案件編號為：` followed by a case identifier, and said the case information was emailed. It offered `以相同資料檢舉其他案件`, `查詢案件進度`, and `完成(清除個人資料)`. Extract the identifier from that receipt and treat it as the authoritative submission result.
4. Retry only after the portal clearly rejects the attempt before creating a case, such as an explicit CAPTCHA validation error. Correct that specific issue, re-observe the challenge if relevant, and make one corrected attempt. If no clear rejection or receipt appears, record `outcome unknown` and inspect the portal's case lookup or authorized receipt evidence before another submission. If ambiguity persists or the same rejection repeats, stop and report the concrete blocker; do not loop.
5. Preserve the receipt tab, capture only its non-sensitive success/identifier region, and report the case number. Keep lookup credentials and verification links out of chat, screenshots, logs, and Git. A closed result tab does not justify submitting again; retain the observed receipt and use case lookup if further verification is needed.

Complete remaining authorized cases independently. A successful Taipei or New Taipei case must not be resubmitted when returning to another pending form. Do not click `完成(清除個人資料)` before preserving the receipt and checking whether the user still needs the session for another authorized case.
