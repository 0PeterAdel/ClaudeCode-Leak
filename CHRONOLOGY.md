# 🕒 Chronology: The "Perfect Storm" of March 31, 2026

The exposure of Claude Code resulted from a multi-step failure chain involving a packaging error and a coincidental North Korean-linked supply chain attack. [15, 16, 17]

| Time (UTC) | Event | Details |
| :--- | :--- | :--- |
| **00:21** | **Axios Compromise** | Malicious versions of `axios` (1.14.1 / 0.30.4) are published via a hijacked maintainer account (`jasonsaayman`). [18, 16] |
| **04:00** | **Claude Code Push** | Anthropic pushes version **2.1.88** to npm. A misconfigured `.npmignore` fails to exclude the 59.8 MB `cli.js.map` file. [2, 10] |
| **04:23** | **Discovery** | Researcher **Chaofan Shou** (@Fried\_rice) identifies the source map and tweets a public link to the `src.zip` archive on Anthropic's R2 bucket. [19, 2, 20] |
| **05:00** | **Viral Spread** | The discovery thread goes viral (16M+ views). Mirrored repositories appear on GitHub and Gitee. [21, 2, 22] |
| **06:00** | **Peak Mirroring** | The repository `instructkr/claude-code` reaches **50,000 stars in under 2 hours**, becoming the fastest-growing repo in history. |
| **08:00** | **Remediation** | Anthropic pulls the package from npm and issues an official statement citing "human error." [8, 7, 23] |
| **12:00** | **Community Ports** | Developer **Sigrid Jin** rewrites the tool in Python (`claw-code`) and Rust to bypass copyright takedowns. |

**Note on the Bun Bug:** The leak was exacerbated by a known bug in the **Bun runtime** (acquired by Anthropic in 2025) which served source maps in production despite documentation claiming otherwise.
