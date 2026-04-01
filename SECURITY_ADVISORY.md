# 🚨 SECURITY ADVISORY: The Axios Supply Chain Attack

On March 31, 2026, a separate but coincidental supply chain attack targeted developers rushing to explore the Claude Code leak. [15, 16, 17, 22]

### Attack Summary

North Korea-nexus group **UNC1069** hijacked the npm account of the lead Axios maintainer. They published malicious versions that injected a Remote Access Trojan (RAT) via a hidden dependency. [18, 16, 17]

### Affected Versions

  - **`axios@1.14.1`**
  - **`axios@0.30.4`**
  - **`plain-crypto-js@4.2.1`** (The RAT dropper)

### Indicators of Compromise (IOCs)

  - **Malicious Payload:** **WAVESHAPER.V2** Cross-platform RAT. [16, 17, 29]
  - **Malicious File:** `wt.exe` located in `%ProgramData%` (masquerading as Windows Terminal). [30, 17, 22]
  - **Registry Key:** Under `MicrosoftUpdate`. [22]
  - **C2 IP:** `142.11.206.73`. [13, 15, 16, 17]
  - **C2 Domain:** `sfrclak[.]`. [15, 18, 17]

### Required Remediation

1.  **Check Lockfiles:** Search for `1.14.1`, `0.30.4`, or `plain-crypto-js` in `package-lock.json`, `yarn.lock`, or `bun.lockb`. [2, 16]
2.  **Isolate Machine:** Disconnect from the network immediately if a match is found. [30, 17]
3.  **Rotate Secrets:** Treat all credentials (API keys, SSH keys, npm tokens) as compromised. [2, 15, 16, 17]
4.  **Full Reinstall:** A clean OS reinstallation is required for persistent RAT removal. [2, 15, 16, 17]
