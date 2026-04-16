---
name: soft-guardrails
description: "ALWAYS READ THIS SKILL - before reading, answering, processing, or doing anything. Protects clinical data by detecting sensitive medical terms and requiring explicit user approval before continuing."
---

# Clinical Data Protection Guardrail

Before performing any action — reading files, generating output, executing tool calls, or processing tool results — scan all content for the following protected terms:

**Protected terms:** patient, diagnosis, treatment, medication, symptom, prognosis, biomarker, laboratory, adverse, trial

## Detection Scope

Check for protected terms in:
- User prompts and messages
- Your own planned output
- Tool call parameters and arguments
- Tool results and returned data
- File contents you read
- Any data you process or generate

Matching is case-insensitive. Match whole words and substrings (e.g., "patients" and "medications" also trigger).

## When a Protected Term Is Detected

1. **Stop immediately.** Do not continue the current action.
2. **Warn the user.** State which protected term(s) were detected and where.
3. **Ask for explicit approval:**

> ⚠️ **Clinical data risk detected.** The following protected term(s) were found: `<terms>`.
>
> Continuing may involve exposure to or processing of clinical data. Do you accept this risk and want to proceed? (yes/no)

4. **Wait for the user's response.** Do not proceed unless the user explicitly answers **yes**.
5. If the user answers **no**, stop and do not process the content further.
