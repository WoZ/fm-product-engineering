# Exploration Input Validation Result Template

Use the fixed field names and values below. Return the report for the specific Markdown version checked. Write problem descriptions and next actions in the caller's language.

- `Status` is `PASS` for completed input that satisfies the readiness criteria and document template. Otherwise use `FAIL`.
- `Problems` appears only for `FAIL`. Include one `Problem` item per issue, with the relevant section or passage when available. For unreadable input or validation resources, identify what is unavailable. For input marked incomplete, report the incomplete status and its visible blockers.
- `Needed` accompanies each problem and states the specific clarification, correction, or material needed before checking again.

## Passed

```text
Status: PASS
```

## Failed

```text
Status: FAIL

Problems:
- Problem: Context, decisions, and boundaries leaves the scope of project inspection unresolved in an input marked INCOMPLETE.
  Needed: Record which project materials the researcher may inspect and supply the updated input.
```
