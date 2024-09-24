# Instructions for Info Assist Deployment
This file documents the steps needed to deploy an instance of Information Assistant to Azure.

It is easiest to deploy from a devcontainer. Open the repository using VSCode, hit CTRL+Shift+P to open the command palette then select `Reopen in container`. This will build a containerised development environment and mount the repo into it.

Log into Azure and select the subscription you will be deploying into. 
```bash
az login
```
This needs to align with the tenancy and subsription defined in `scripts/environments/local.env`. We're currently deploying into `MPN-Central`, if you choose another subscription it is expected that additional configuration will be required that is not  documented here at present.

Deploy the terraform stack by running
```bash
make deploy
```
Once deployed, the web app needs to be manually configured to disable authentication.
Navigate to the `infoasst-web-XXXXX` resource in the console, go to `Settings` -> `Authentication` then click `Edit` next to `Authentication Settings` and disable `App Service authentication`.

The instance should now be configured for compatibility with the training exercises.
