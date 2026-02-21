---
applyTo: ".github/workflows/**"
---

- **`curl --fail` is sufficient validation**: Do not suggest adding pre-validation API calls before `curl` downloads. The `--fail` flag causes `curl` to exit with a non-zero status on HTTP errors, and GitHub Actions terminates the step on failure. Additional URL existence checks are redundant.
- **Intentional use of latest upstream releases**: Workflows that track upstream releases (e.g., fetching the latest tmux tarball) do so intentionally. Do not suggest pinning to a specific commit or verifying checksums when the workflow's purpose is to detect and respond to new releases. Changes are submitted as PRs for human review before merging.
