# NaaVRE Virtual Lab Action

## How to use

Add a file named `.github/workflows/virtual-lab.yaml` to your repository:

```yaml
name: Build, test and publish Virtual Lab
on:
  push:
  release:
  pull_request:

permissions:
  packages: write
  pull-requests: write

jobs:
  binder:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - uses: NaaVRE/virtual-lab-action@main
        with:
          registry_password: ${{ secrets.GITHUB_TOKEN }}
```
