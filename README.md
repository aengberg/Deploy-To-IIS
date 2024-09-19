# Deploy-To-IIS

## How to use
Github Action that deploys to IIS using powershell and WebAdministration-module
Steps done in script:
- The action copies the whole webroot directory from the IIS-site to a new directory
- Copies the files from the package directory to the new directory
- Set new directory path to IIS-site

```yaml
name: "Deploy to IIS"
on: [push]

jobs:
  deploy:
  runs-on: windows
  steps:
  - uses: aengberg/Deploy-To-IIS@v1.0.0
    with:
        sourcepath: "${{ github.workspace }}/folder"
        sitename: "web-public"
        useappoffline: false
        retentionPolicyName: "web-public-1.0*"
        retentionPolicyCount: 3
```