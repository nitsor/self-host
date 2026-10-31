# Security policy

Thank you for helping keep Nitsor and its users safe.

## Reporting a vulnerability

Report security problems **privately**. Do not open a public issue, pull request or discussion. Do not include working credentials, personal data or customer data in your report.

- **Email:** [security@nitsor.com](mailto:security@nitsor.com)
- **Fallback:** if you cannot send email, use the contact form at <https://nitsor.com/contact> and start your message with "Security".

A useful report includes:

- the self-host release version (`v<version>`, from `release.txt` or the minisign trusted comment) and, if relevant, the image digest from `compose.yaml`;
- the vulnerability and what an attacker could do with it, including any access they would need first;
- steps, a proof of concept or code that shows the problem;
- whether you believe it is being **actively exploited**;
- any fix or mitigation you suggest;
- how you would like to be credited.

## What happens next

- We acknowledge your report within **3 business days**.
- We confirm or rule out the problem, keep you informed while we investigate, and agree a disclosure date with you.
- For a confirmed critical vulnerability, we aim to release a fix or mitigation within **30 days** of confirming it.
- We publish an advisory when a fix is available. Where possible we use a GitHub Security Advisory, which is machine-readable and can carry a CVE.

## Coordinated disclosure

Please give us a reasonable time to fix the problem before you disclose it publicly. We will agree a date with you: by default **90 days** after your report, or earlier once a fix is available. If a vulnerability is being actively exploited, we may publish sooner to protect users.

## Supported versions

Nitsor has not published a release yet. Once releases are published, security fixes are provided for **the latest release**.

| Product | Supported with security fixes |
|---|---|
| Self-host bundle (`nitsor/self-host` releases) | Latest release |
| Hosted service (app.nitsor.com) | Always the current version |

## Safe harbour

If you make a good-faith effort to follow this policy, we consider your research authorised. We will not take legal action against you or report you to law enforcement for it, and we will work with you to understand and resolve the problem. Good faith means you:

- test only against your own installation or accounts, never other users' data or workspaces;
- do not degrade, disrupt or destroy service or data;
- stop and tell us as soon as you reach data that is not yours, and do not keep or share it;
- give us reasonable time to fix the problem before disclosing it.

## Credit

We credit reporters in the advisory unless you ask us not to. We do not run a paid bug bounty at this time.

## EU Cyber Resilience Act

For Nitsor products with digital elements made available on the EU market, Nitsor reports actively exploited vulnerabilities and severe incidents under Article 14 of Regulation (EU) 2024/2847 (the Cyber Resilience Act), through ENISA's single reporting platform, and informs affected users. Please tell us if you have seen exploitation: it helps us meet those deadlines.

## Verifying releases

Every release is signed with the Nitsor release key `F1819173358F3BE4` (see [README.md](README.md#verify)). A release that does not verify is not a Nitsor release: report it to us as a security problem.

## Third-party components

The bundle runs Convex backend and dashboard images published by Convex. Report vulnerabilities in those images to Convex as well as to us.
