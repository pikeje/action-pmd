# PMD Source Code Analyzer Action

This action allows to use PMD Source Code Analyzer from GitHub Actions and fixes a small issue regarding permissions. It is forked from 
[https://github.com/sfdx-actions/setup-pmd](https://github.com/sfdx-actions/setup-pmd). Check their action out. Most of the documentation will remain the same. 

## Example usage

```yaml
name: PMD Analysis

on: [push]

jobs:
  pmd:
    name: 'Run PMD'
    runs-on: ubuntu-latest
    
    steps:
      - name: Setup JRE
        uses: actions/setup-java@v1
        with:
          java-version: '13.0.2'
          java-package: jre
          architecture: x64

      - uses: mcanog/setup-pmd@v1
      - name: run-pmd
        run: pmd -d <source code> -R <ruleset> -f xml --failOnViolation false > report.xml
```