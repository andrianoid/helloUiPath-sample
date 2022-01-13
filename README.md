# HelloUiPath!

This project is a sample 'Hello World' project for UiPath that includes a 'buildAndDeploy' workflow for GitHub Actions.

## UiPath Project

The UiPath project accepts two input arguments:
  
- `in_greeting`  
- `in_name`

The process will simply log a message in the format:

	in_greeting + " " + in_name + "!!!!"

There are three simple test cases that are published:
  
- `EnglishCase`  
- `FrenchCase`  
- `SpanishCase`  

## GitHub Actions Environment

### Tools / Prerequisites

In these example workflows, **Orchestrator Authentication** is handled with [External Applications](https://docs.uipath.com/automation-cloud/docs/managing-external-applications). 

[UiPath CLI](https://www.myget.org/feed/uipath-dev/package/nuget/UiPath.CLI) is used for Pack and Deploy functionality. It is light-weight and no installation is required.

A [GitHub-hosted runner](https://docs.github.com/en/actions/using-github-hosted-runners/about-github-hosted-runners) (windows-latest) is used to run the workflows.

The following **'Secrets' are required** in your GitHub repository Settings -> Secrets:

- **`TEST_TENANT_NAME`** - _Target Cloud Orchestrator Tenant for Automated Tests_
- **`UAT_TENANT_NAME`** - _Target Cloud Orchestrator Tenant for Process Package (UAT)_
- **`ACCOUNT_NAME`** - _Target Cloud Orchestrator Account Name_ 
- **`OAUTH_CLIENT_ID`** - _App ID of External Application_
- **`OAUTH_CLIENT_SECRET`** - _App Secret of External Application_
- **`OAUTH_CLIENT_SCOPES`** - _Required scopes granted to External Application_




## GitHub Actions Workflows


### Build And Deploy (Process) - [UiPathBuildDeploy.yml](.github/workflows/UiPathBuildDeploy.yml) 

  

##### Required Oauth Scopes:     
  
- `OR.BackgroundTasks`   
- `OR.Execution`   
- `OR.Folders`   
- `OR.Settings`

##### Workflow Steps

- **Build process package** (`uipcli`)    
- **Deploy to cloud orchestrator** (`uipcli`)    



### Build, Deploy And Run (Tests) - [UiPathBuildDeployRun-Tests.yml](.github/workflows/UiPathBuildDeployRun-Tests.yml)    

##### Required Oauth Scopes:     
- `OR.Assets`   
- `OR.BackgroundTasks`   
- `OR.Execution`   
- `OR.Folders`   
- `OR.Folders.Read`   
- `OR.Jobs`   
- `OR.Machines`   
- `OR.Monitoring`   
- `OR.Robots`   
- `OR.Settings`   
- `OR.Settings.Read`   
- `OR.TestSetExecutions`   
- `OR.TestSets`   
- `OR.Users`
  
##### Workflow Steps

- **Build test package** (`uipcli`)  
- **Deploy to cloud orchestrator** (`uipcli`)    
- **Create test set** (`powershell`)
    - Get Access Token
    - Get Folder Id
    - Get Release
    - Get Test Case Definitions
    - Create test Set
    - Execute Test Set  

