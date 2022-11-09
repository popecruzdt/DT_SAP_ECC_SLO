# DT_SAP_ECC_SLO
Dynatrace SLO management using Monaco for SAP ECC

![Screenshot](https://raw.githubusercontent.com/popecruzdt/DT_SAP_ECC_SLO/main/DT_SAP_ECC_SLO_Diagram.png)

## Summary:
This is a configuration template to create and manage Dynatrace SLO using Monaco for SAP ECC applications.

## Prerequisites:
  * SAP ECC (ABAP) Instance monitored with SAP Application Server Extension
    * https://www.dynatrace.com/hub/detail/sap-abap/overview/?query=sap

## Deployment Steps:
### Manually define user-session custom metrics
  * Metric Name: `uscm.sap_gui_modules_<sap_module_name>_sessions`

### Prepare Monaco:
Download/Install Monaco:
  * https://dynatrace-oss.github.io/dynatrace-monitoring-as-code/Get-started/installation
Clone Repo:
  * git clone https://github.com/popecruzdt/DT_SAP_ECC_SLO.git
Modify environments.yaml:
  * Update values to match your Dynatrace environment
Generate Access Token:
  * `Read SLO`, `Write SLO`, `Access problem and event feed, metrics, and topology`, `Read configuration`, `Write configuration`
Set environment variable:
  * Linux/MacOS: `export TOKEN_VAR_NAME=dt0c01.*`
  * Windows: `set TOKEN_VAR_NAME=dt0c01.*`

### Modify Projects
Create new project for SAP application
  * Duplicate/clone `APP_NAME` directory
  * Rename copy of `APP_NAME` directory to the name of the SAP application (avoid spaces)
  * Find and replace `APP_NAME` in all yaml files with the name of the SAP application (avoid spaces)

### Deploy Project
```
 monaco -e=environments.yaml -p=projects/SAP_ECC/YOUR_APP_NAME
```
