# org-custom-actions
A Github composite action to make it slightly less verbose to use private custom actions in your organization's github repo

This repo is public, because inception. To use:

```yaml
name: My Greatest Workflow

jobs:
  do_stuff:
    steps:
      - uses: sesamecare/org-custom-actions@v1
        with:
          token: ${{ secrets.GITHUB_TOKEN }}

      # Use any of your custom actions
      - name: Some Custom Action
        uses: ./.github/actions/some-custom-action
```

```