# sast_gitleaks
Static Application Security Testing using GitLeaks

Reusable Workflow v.1.0.0

Call example:

```
name: Static application security testing
on:
  workflow_dispatch:
jobs:
  sast_semgrep:
    permissions:                                                                         
      contents: read
    uses: ramshackle-code/sast_semgrep/.github/workflows/sast_gitleaks.yml@[<version-tag> or <commit-sha>]
    secrets:
      token: ${{ secrets.GITHUB_TOKEN }}
```

Optinal parameters

```
     uses: ramshackle-code/sast_semgrep/.github/workflows/sast_gitleaks.yml@[<version-tag> or <commit-sha>]
     with:
       timeout-minutes: <minutes>     #Execution timeout. Default value 5 minutes
       gitleaks-version: <image tag>  #GitLeaks version. Default 8.16.1
       runs-on: <runner label>        #Runner Label. Default 'ubuntu-latest'
```
