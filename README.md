# Sigma Detection Rules

A collection of hand-written Sigma rules covering common attack techniques across
multiple MITRE ATT&CK tactics. Each rule is written manually — field by field,
tag by tag — rather than generated or copied, as part of building detection
engineering skills toward Incident Response and cloud security work.

## Why this repo exists

I'm a SOC L1 Analyst working daily with Sentinel, Defender, CrowdStrike, and
Carbon Black. This repo is where I build detection engineering depth beyond
day-to-day alert triage — writing Sigma rules from first principles, verifying
every field and access-rights value against primary sources rather than
copying existing rulesets, and reasoning through false positives from actual
operational experience rather than generic placeholders.

## Rules

| Rule | ATT&CK Technique | Tactic | Status |
|---|---|---|---|
| [MS Office Suspicious Child Process Creation](rules/office-child-process.yml) | T1059.001 / T1059.003 / T1059.005 | Execution | experimental |
| [LSASS Memory Dump Detection](rules/lsass-memory-dump.yml) | T1003.001 | Credential Access | experimental |
| [New Scheduled Task via schtasks.exe or PowerShell](rules/schtasks-scheduled-task.yml) | T1053.005 | Persistence | experimental |

*(table grows as rules are added)*

## Methodology

Each rule follows the same process:

1. Identify the technique from MITRE ATT&CK and confirm the tactic/technique ID.
2. Confirm logsource category/product against the Sigma taxonomy appendix.
3. Verify field names and values (e.g. access-rights hex masks) against primary
   sources — Microsoft documentation, Sysmon references, or real telemetry —
   rather than assuming or copying.
4. Write detection logic and manually trace the boolean condition to confirm
   it matches the intended behavior.
5. Write false positives based on reasoned, specific scenarios rather than
   generic categories.

## Status

Actively maintained — new rules and refinements added incrementally as
coverage expands across more ATT&CK tactics.