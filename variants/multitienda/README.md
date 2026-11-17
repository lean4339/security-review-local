# Security Review · Local & Marketplace — multitienda

**Review concrete code changes, build meaningful tests and learn from the evidence.**

**English** · [Español](README.es.md)

A snapshot of the local security-review skill, including changes that are absent from its published repository. Marketplace variants are preserved separately because their content and distribution terms differ.

This directory preserves the multitienda edition. Its own SKILL.md and terms are authoritative for this snapshot; features described for the repository root may differ.

[Repository overview](../../README.md)

## What it covers

| Area | Guidance |
| --- | --- |
| Commit review | Resolve the requested revision and distinguish committed code from working-tree changes. |
| Development and tests | Connect authorization boundaries, untrusted input and failure behavior with relevant functional and security checks. |
| Learning | Use OWASP references and exercises for web applications, MCP, LLMs and agents. |

## Start here

Read [SKILL.md](SKILL.md), then the references relevant to the task. Give a compatible agent access to this package and the authorized target files. Keep adjacent directories with SKILL.md; copying that file alone can break its references.

### Requirements

A compatible agent and an authorized target project for code work. Teaching can start without a repository. The skill asks the agent to verify the applicable OWASP edition when invoked; the packaging step did not perform that research.

### Example request

> Use security-review on this commit. Resolve its full SHA, inspect the authorization boundary and propose a regression test that distinguishes the vulnerable behavior from the corrected behavior.

## Package contents

| Path | Purpose |
| --- | --- |
| [SKILL.md](SKILL.md) | Agent instructions and task workflow |
| [references](references) | Supporting modules and sources |
| [agents](agents) | Client-facing skill metadata |
| [START-HERE.txt](START-HERE.txt) | Original distribution entry point |

### Reference index

- [OWASP para MCP, LLM, agentes y skills](references/ai-security.md)
- [Estudio, ejercicios y cuestionarios](references/learning.md)
- [Fuentes y técnicas OWASP](references/owasp.md)
- [Tests de funcionamiento y de seguridad](references/security-tests.md)

## Scope and limits

This is an instruction package, not an automatic scanner or security certification. Session-level commit follow-up does not install a background watcher. The root includes the local auth-boundaries reference; older marketplace variants retain their own contents. External evaluation suites are outside this package.

The README is available in English and Spanish, matching Huella’s documentation. Original SKILL.md files and references retain their source language and wording.

## Source and terms

Original documents for this edition: [LICENSE.txt](LICENSE.txt) · [NOTICE.txt](NOTICE.txt).

Prepared from Leandro Ayala’s local skill files on 2026-11-17. This README adds documentation; it does not replace original terms or add a license.
