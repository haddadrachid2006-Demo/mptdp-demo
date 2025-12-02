# Mail Pre-Flight Template Discovery Protocol (MPTDP)

> **🔴 STATUS: OFFICIAL IETF INTERNET-DRAFT (Active)**
> **Reference:** `draft-haddad-mptdp`

## 📄 Overview

This repository hosts the official **Proof of Concept (POC)** for the **MPTDP** standard, submitted to the IETF on November 27, 2025.

**The Problem:** Incoming emails (B2B/B2C) are often unstructured, missing key data, and costly to process.
**The Solution:** MPTDP allows Mail User Agents (MUA) to proactively fetch a structured JSON template from the recipient's domain *during* address typing, before the message is sent.

---

## 🔗 Quick Links

*   **📜 Read the Official Standard (IETF):** [datatracker.ietf.org/doc/draft-haddad-mptdp/](https://datatracker.ietf.org/doc/draft-haddad-mptdp/)
*   **💻 Try the Live Demo:** [haddadrachid2006-demo.github.io/mptdp-demo/](https://haddadrachid2006-demo.github.io/mptdp-demo/)

---

## 🚀 Key Features Demonstrated

This POC simulates a full MPTDP environment (Server & Client side) with the following capabilities:

1.  **Privacy-by-Design:** The client checks a Manifest (`/.well-known/mptdp-manifest.json`) before requesting templates.
2.  **Smart Append:** Injected templates do not overwrite user-generated content.
3.  **Hard Validation:** The protocol can enforce `required: true` fields, blocking the send button if data is missing.
4.  **Dynamic Switching:** Real-time template swapping based on the recipient address (e.g., `support@` vs `jobs@`).

## 🛠️ Technical Stack

*   **Protocol:** HTTPS / JSON
*   **Discovery Path:** `/.well-known/mptdp`
*   **Security:** Signature verification (Simulated in POC)

  ## 📘 Documentation

- 🇫🇷 [FAQ Technique (Français)](FAQ-fr.md)
- 🇬🇧 [Technical FAQ (English)](FAQ-en.md)


## © Copyright & License

**Concept & Specification:** Rachid HADDAD.
**Code:** MIT License.

*This code is provided for demonstration purposes to support the IETF Draft discussion.*
