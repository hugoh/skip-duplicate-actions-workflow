# Re-usable [skip-duplicate-actions](https://github.com/marketplace/actions/skip-duplicate-actions) workflow

This repository is purely set up to reuse a [skip-duplicate-actions](https://github.com/marketplace/actions/skip-duplicate-actions) workflow:

```yaml
---
name: Example

jobs:
  pre_job:
    # yamllint disable-line rule:line-length
    uses: hugoh/skip-duplicate-actions-workflow/.github/workflows/skip-duplicate-actions.yml@master
    permissions:
      actions: write
      contents: read

  real_job:
    needs: pre_job
    if: ${{ needs.pre_job.outputs.should_skip != 'true' }}
    ...
```

See [GitHub's workflow reuse documentation](https://docs.github.com/en/actions/using-workflows/reusing-workflows) for more details.
