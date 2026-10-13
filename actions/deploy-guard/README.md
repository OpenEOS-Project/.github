# deploy-guard

Composite action used by the production deploy jobs of `openeos-api`,
`openeos-web`, `openeos-shop`, `openeos-docs` and `openeos-landing`.

Before a deploy it asks the API whether an event is selling right now
(`GET /api/internal/deploy-guard`, bearer token `DEPLOY_GUARD_TOKEN`):
an active event with at least one real (non-test) order in the last
30 minutes. While that is the case the job waits and asks again every
5 minutes; after 90 minutes it fails with a message.

```yaml
- uses: OpenEOS-Project/.github/actions/deploy-guard@main
  with:
    token: ${{ secrets.DEPLOY_GUARD_TOKEN }}
    url: ${{ vars.DEPLOY_GUARD_URL }}   # optional
    force: ${{ inputs.force }}           # workflow_dispatch input
```

| Answer | Result |
|--------|--------|
| `busy: false` | deploy continues |
| `busy: true`, 5xx, timeout | wait 5 min, ask again; fail after 90 min |
| 401 / 403 | fail at once (token mismatch) |
| 404 | warn and continue (API without the endpoint, or token not set on the server) |
| no token / `force: true` | warn and continue |

Event names are not written to the log: the logs of public repositories
are public.
