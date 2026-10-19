# agent-bridge-releases

`agent-bridge.sha` holds the commit sha of the latest agent-bridge build whose images were published to GHCR.

- Written by the publish workflow in `AgentsHubFabric/agent-bridge` through a deploy key limited to this repo.
- Read by a scheduled workflow in `InitOpsLab/argocd-ops`, which validates it (40 hex characters) and bumps the image tags there.
- Public on purpose so that `argocd-ops` needs no credential to read it. It holds no secrets: a commit hash only.
