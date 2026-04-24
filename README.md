# 2026-04-urag-krishnaik-bootcamp

## Meta Workflows

Opinionated workflows for managing the project matrix via `meta`.

### Branching

All feature work originates from an up-to-date `develop` branch. Don't fall behind.

```bash
# Fast-forward develop and spin up your feature branch across all repos
meta exec "git checkout develop && git pull origin develop && git checkout -b <feature-branch>"
```

### Repository Governance (`meta-gh`)

Use the `meta-gh` plugin to enforce consistent repository configurations across all projects.

```bash
# 1. Set 'develop' as the default branch universally
meta gh repo edit --default-branch develop

# 2. Lock down 'develop' with branch protection (requires 1 approving review, no force pushes)
meta gh api -X PUT repos/:owner/:repo/branches/develop/protection \
  -f enforce_admins=true \
  -f required_status_checks=null \
  -f restrictions=null \
  -F required_pull_request_reviews="{\"required_approving_review_count\":1,\"dismiss_stale_reviews\":true}"
```
