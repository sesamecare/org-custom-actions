# org-custom-actions
A Github composite action to make it slightly less verbose to use private custom actions in your organization's github repo. Inspired by [this post](https://www.julianburr.de/til/using-a-monorepo-for-your-custom-github-actions/) which makes it a *lot* easier to share action code in an organization where private workflow steps are often necessary.

{% note %}

**Note:** The default GITHUB_TOKEN is scoped to your repo, so you can't typically use this to checkout another private repo. You need a personal access token with appropriate permissions (I would suggest limiting it to the actions repo and adding it as an organization secret like GITHUB_ACTION_REPO_TOKEN or some such).

{% endnote %}

This repo is public, because inception. To use:

```yaml
name: My Greatest Workflow

jobs:
  do_stuff:
    steps:
      - uses: sesamecare/org-custom-actions@v1
        with:
          token: ${{ secrets.GITHUB_PAT_TOKEN }}

      # Use any of your custom actions
      - name: Some Custom Action
        uses: ./.github/actions/some-custom-action
```

```