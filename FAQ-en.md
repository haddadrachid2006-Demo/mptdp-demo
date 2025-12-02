🛡️ MPTDP – Technical FAQ & Architecture Defense

Reference: draft-haddad-mptdp
Status: Individual Internet-Draft (not yet WG-adopted)

1. Why not just use a web form?

Web forms force the user to break context:

switching to the browser

filling a remote form

coming back to the email

👉 MPTDP keeps the user inside their primary workflow: the email client.

We preserve:

conversation threads

signatures

native archiving

user habits

while enforcing structured JSON data.

2. Is there a risk of email enumeration?

No.

MPTDP uses a Privacy Manifest:

/.well-known/mptdp-manifest.json

This file lists the only public email endpoints that are allowed to expose templates.

👉 MPTDP clients must not query unlisted addresses.
GDPR-friendly, privacy-by-design.

3. What happens if the server is down?

Fail-Safe behavior:

manifest unreachable

API fails

HTTPS failure

👉 The client falls back to standard email mode, no blocking.

4. What is the link between MPTDP and AI?

LLMs struggle with:

ambiguous text

messy human emails

incomplete information

MPTDP forces the human to provide typed, structured JSON up front.

Results:

AI agents can process the request reliably

CRMs (Salesforce, ServiceNow, PEGA) ingest data instantly

zero hallucination risk

👉 MPTDP bridges human intent and AI automation.

5. How do you prevent phishing (fake templates)?

The protocol supports:

mandatory HTTPS

digital signatures on JSON payloads (DKIM-like)

a public verification key in DNS or manifest

Attackers cannot forge a valid template without the domain’s private key.

6. Can we generate a unique ticket ID?

Yes, and it is recommended.

Example:

"ticket_id": "MPTDP-20250201-ABC123"


Possible generators:

the add-in

the SaaS (recommended)

the template

the backend

The SaaS enables full traceability and auditing.

7. Does MPTDP modify SMTP?

No.

MPTDP is a pre-flight HTTP protocol executed before SMTP.

The final email is a standard SMTP message with:

JSON in the body (HTML comment)

or a .json attachment

or an X-MPTDP header (enterprise mode)

Compatible with all existing infrastructures.

8. What happens if the recipient is not MPTDP-enabled?

Nothing special.

They receive a normal email.

Backward compatibility is 100%.

9. How does MPTDP become a global standard?

Standardization path:

Innovation & POC – done

Internet-Draft publication – done (draft-haddad-mptdp)

Working Group adoption – pending

Vendor implementation (Microsoft, Google)

Potential RFC

The protocol is already usable in production today.

10. Does MPTDP require an Outlook add-in?

No.

It can work via:

browser extensions

standalone clients

simple JSON injection

The add-in is recommended for UX, but not required.

© 2025 – Rachid H., MPTDP Project
