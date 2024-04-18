# sast_gitleaks
Static Application Security Testing using GitLeaks

Reusable Workflow v.1.3.0

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
       gitleaks-version: <image tag>  #GitLeaks version. Default 8.18.2
       runs-on: <runner label>        #Runner Label. Default 'ubuntu-latest'
       gitleaks-config: <config file> #Gitleaks config file. Default 'cfg/gitleaks.toml'
       fetch-depth: <depth>           #Fetch Depth. Deafult 1 actual commit 0 all commits
```

Exceptions

In order to avoid false positive you can put a file called `.gitleaksignore.yml` in your repo root folder with the hash, file and line to exclude.
Example:

```
19afb0df830fdeddea7efa323cefddfcc9d27927:docs/tec/tec_blogawsparte1.md:private-key:108
```
