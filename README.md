# HelloUiPath!

This project is a sample 'Hello World' project for UiPath that includes a 'buildAndDeploy' workflow for GitHub Actions.

## GitHub Actions - BuildAndDeploy

A basic [Build and Deploy YML file](.github/workflows/UiPathBuildDeploy.yml) is included that will build the nuget package from your project, and will deploy it to a cloud orchestrator. Orchestrator Authentication is handled with [External Applications](https://docs.uipath.com/automation-cloud/docs/managing-external-applications). 

> Note: [UiPath CLI](https://www.myget.org/feed/uipath-dev/package/nuget/UiPath.CLI) is used for Pack and Deploy functionality. Other functions - including other authentication mechanisms - are supported by the CLI as well. 

`UiPathBuildDeploy.yml` is run on a [GitHub-hosted runner](https://docs.github.com/en/actions/using-github-hosted-runners/about-github-hosted-runners) (windows-latest).

The following **'Secrets' are required** in your GitHub repository Settings -> Secrets:

- **`TENANT_NAME`** - _Target Cloud Orchestrator Tenant_
- **`ACCOUNT_NAME`** - _Target Cloud Orchestrator Account Name_ 
- **`OAUTH_CLIENT_ID`** - _App ID of External Application_
- **`OAUTH_CLIENT_SECRET`** - _App Secret of External Application_
- **`OAUTH_CLIENT_SCOPES`** - _Required scopes granted to External Application_
	> Note: the following application scopes are required for the `package deploy` function:   
	> **OR.BackgroundTasks OR.Execution OR.Folders OR.Settings**

