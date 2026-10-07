# NaaVRE Virtual Lab Action

## How to use

Create a new actions secret on your virtual lab repository (your repo > Settings > Secrets and variables > Actions > New repository secret), named `NAAVRE_BUILD_TOKEN`. Use the token received by your NaaVRE operator. (For NaaVRE operators: create a new NaaVRE-environment-service token for each repository.)

Next, add a file named `.github/workflows/virtual-lab.yaml` to your repository:

```yaml
name: Build, test and publish Virtual Lab
on:
  push:
    branches:
      - '**'
  release:
    types: [published]

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
          naavre_build_token: ${{ secrets.NAAVRE_BUILD_TOKEN }}
```
