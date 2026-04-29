---
name: delivery-materials
description: Create or update formal software project delivery materials for any project, especially user manuals, functional test documents, performance test documents, test acceptance reports, O&M manuals, and Markdown/Word deliverables derived from Git commits, interface changes, Web features, API documentation, screenshots, or user-provided scope notes. Use when Codex needs to lock delivery scope, write owner-facing/compliance-oriented Chinese delivery documents, add screenshot placeholders for UI manuals, or later embed screenshots from a specified image directory into Word documents.
---

# Delivery Materials

## Core Workflow

1. Lock the delivery scope first.
   - Prefer the user's explicit scope, commit list, commit screenshot, issue list, changed APIs, changed pages, acceptance notes, or existing interface documentation.
   - If using Git, inspect commit titles and changed controllers/pages/services/SQL/mappers/DTOs, then exclude unrelated commits and other people's unrelated work.
   - Do not silently include historical modules, old interfaces, or nearby code that is outside the requested batch.
2. Identify the project name and naming convention.
   - Use the user's provided project name exactly.
   - If the source code path or repository name conflicts with the user's project name, prefer the user's explicit name in external-facing materials.
3. Split deliverables by audience and evidence.
   - `用户使用手册`: user-facing Web workflows, API calling procedures, permissions, prerequisites, results, and screenshot placeholders.
   - `功能测试`: black-box and white-box tests.
   - `性能测试`: business-facing performance scenarios and code-side performance review points.
   - `测试验收报告`: scope, basis, verification, compliance, and sign-off conclusion.
   - `运维手册`: environment, deployment, configuration, monitoring, logs, backup, rollback, and fault handling.
4. Produce one Markdown file per document unless the user asks for a single combined file.
5. When Word output is requested, generate one `.docx` per Markdown file by default. Do not combine documents unless the user explicitly asks.

## Writing Defaults

1. Write in a formal owner-facing Chinese style suitable for delivery, acceptance, and reporting.
2. Prefer a compliance and management narrative over internal R&D notes.
3. Keep wording concise, stable, and business-readable.
4. Remove internal traces from final delivery documents unless the user asks for an internal draft.
   - Avoid source-code path lists in the main body.
   - Avoid commit hashes in the formal body.
   - Avoid `初稿`、`待补充`、`没做`、`待联调` and similar placeholder wording in final versions.
   - Avoid secrets, passwords, tokens, API keys, database credentials, and private server passwords.
5. If a credential reference is necessary, point to the user's controlled credential file and keep the value masked.

## User Manual Rules

1. Cover real user-facing behavior.
   - For Web features, write role, menu path, prerequisites, operation steps, expected result, and screenshot placeholder.
   - For pure API/open-interface features, write caller role, base URL, request headers, parameters, request examples, response structure, error handling, and result handling.
2. If a page or workflow needs screenshots and the screenshots are not available yet, add explicit placeholders.
   - Use this placeholder format in Markdown:
     `【截图占位：<编号>-<页面或步骤名称>，建议文件名：<编号>-<简短英文或拼音名>.png】`
   - Keep placeholders near the relevant operation step, not in a separate appendix only.
3. Ask the user for or infer a screenshot directory when embedding screenshots later.
   - Recommended directory: a `screenshots/` folder next to the generated documents.
   - Match images by the placeholder number or suggested filename.
   - If an image is missing, leave the placeholder text in place and list missing screenshots in the final response.
4. Do not invent screenshots. Use placeholders until real images exist.

## Interface Manual Detail

For API/open-interface user manuals, include these sections where applicable:

1. Overall calling flow.
2. Environment and base address.
3. Authentication and required headers.
4. Common request and response structure.
5. Parameter tables for each endpoint.
6. Request body examples.
7. Important response fields.
8. Empty-data handling.
9. Permission, validation, and business error handling.
10. Recommended logging/audit fields for the caller.

## Test Document Rules

### 功能测试

- Must include both `黑盒测试` and `白盒测试`.
- Black-box coverage should include interface/page availability, request and response correctness, parameter validation, business rules, permission and data-scope behavior, export/query correctness, and empty-data behavior.
- White-box coverage should include business branch coverage, exception paths, service/data linkage, transaction or persistence behavior, authorization isolation, logging, and audit paths.

### 性能测试

- Include business scenarios and code-side review points.
- Cover concurrency, response time, throughput, pagination or export behavior, large result sets, database hotspot risk, cache or report-service dependencies, and failure/timeout behavior when relevant.
- Keep the language report-like rather than exploratory.

### 测试验收报告

- Summarize project scope, acceptance basis, environment, function verification, performance verification, compliance checks, residual risks, and acceptance conclusion.
- The conclusion should be suitable for sign-off.

### 运维手册

- Cover system description, environment matrix, account/credential management, branch/version requirements, deployment steps, interface/platform dependencies, monitoring, log inspection, common faults, backup, rollback, and security notes.
- Do not expose cleartext secrets. Refer to controlled credential documents instead.

## Word Output Rules

1. Generate one Word document per Markdown document unless the user asks for a combined version.
2. Strip Markdown syntax from headings; Word titles must not include leading `#`.
3. Default Word body style: `宋体` `小四`.
4. Default heading style: `黑体`, with clear heading levels.
5. Use visible table borders, readable cell padding, and stable table header styling.
6. Preserve code blocks and request examples in a monospace font.
7. If screenshot placeholders exist and images are available, embed each image near its placeholder and keep captions.
8. If images are unavailable, keep the placeholder visible.

## Screenshot Embedding Workflow

When the user says screenshots are ready:

1. Locate the generated Markdown/Word files and the screenshot directory.
2. List screenshot files and match them to placeholders by:
   - placeholder number, then
   - suggested filename, then
   - nearby page or step name.
3. Insert screenshots into the matching Word documents after the relevant step or caption.
4. Use consistent image width that fits the page, usually 13-15 cm for full-page screenshots.
5. Keep captions such as `图 1 项目列表页面`.
6. Report inserted count and missing placeholders.

## Output Naming

Use stable Chinese filenames unless the user provides another convention:

- `00-交付材料范围说明.md`
- `01-用户使用手册.md`
- `02-功能测试.md`
- `03-性能测试.md`
- `04-测试验收报告.md`
- `05-运维手册.md`

Corresponding Word files should use the same base name with `.docx`.

## References

- Read `references/doc-outlines.md` when document structure is needed.
