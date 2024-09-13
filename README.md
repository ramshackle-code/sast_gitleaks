## sast_gitleaks

# Static Application Security Testing using GitLeaks

## Call example:

```
name: LEAKS
on:
  pull_request:
    branches-ignore:
      - main
    paths-ignore:
      - '.github'
jobs:
  sast_gitleaks:
    permissions:                                                                         
      contents: read
    uses: ramshackle-code/sast_gitleaks/.github/workflows/sast_gitleaks.yml@0de5a68b4c898df6928e8913759357d5e95a86a6  #v1.3.1
    secrets:
      token: ${{ secrets.GITHUB_TOKEN }}
```

## Optinal parameters

```
     uses: ramshackle-code/sast_gitleaks/.github/workflows/sast_gitleaks.yml@[<version-tag> or <commit-sha>]
     with:
       timeout-minutes: <minutes>     #Execution timeout. Default value 5 minutes
       gitleaks-version: <image tag>  #GitLeaks version. Default 8.18.4
       runs-on: <runner label>        #Runner Label. Default 'ubuntu-latest'
       gitleaks-config: <config file> #Gitleaks config file. Default 'cfg/gitleaks.toml'
       fetch-depth: <depth>           #Fetch Depth. Deafult 1 actual commit 0 all commits
```

## Configuration

You need to create config file in `cfg` path.
Please, use this [config file](https://github.com/gitleaks/gitleaks/blob/e93a7c0d2604fd1bcc43ac9cac6144a62387a8a4/config/gitleaks.toml) as an example.

## Exceptions

In order to avoid false positive you can put a file called `.gitleaksignore.yml` in your repo root folder with the hash, file and line to exclude.
Example:

```
19afb0df830fdeddea7efa323cefddfcc9d27927:docs/tec/tec_blogawsparte1.md:private-key:108
```
