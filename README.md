# HelloUiPath!

This project is a sample 'Hello World' project for UiPath that includes a 'buildAndDeploy' workflow for GitHub Actions.

## GitHub Actions - BuildAndDeploy

A basic Build and Deploy YML file is included that will build the nuget package from your project, and will deploy it to a cloud orchestrator. The following 'Secrets' are required in your repository Settings -> Secrets:

- TENANT_NAME
- USER_KEY
- ACCOUNT_NAME
