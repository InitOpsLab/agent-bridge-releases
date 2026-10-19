# agent-bridge-releases

**This repository holds one thing: a commit hash.** Nothing else may live here.

`agent-bridge.sha` is a single line of 40 hex characters: the commit of the latest agent-bridge build whose
images were published to GHCR.

Allowed contents, exactly: `agent-bridge.sha` and this `README.md`. No workflows, no scripts, no other files.

- Written by the publish workflow in `AgentsHubFabric/agent-bridge` through a deploy key limited to this repo.
- Read by a scheduled workflow in `InitOpsLab/argocd-ops`. Before it uses the value, it checks that the repository
  tree contains exactly those two files and that the hash line is valid; if anything else is present, it deploys
  nothing and fails.
- GitHub Actions is disabled here and history is append-only (no force pushes or deletions).
- Public on purpose so `argocd-ops` needs no credential to read it. It holds no secrets.
