# HelloUiPath!

This project is a sample 'Hello World' project for UiPath that includes a 'buildAndDeploy' workflow for GitHub Actions.

## UiPath Project

The UiPath project accepts two input arguments:  
- `in_greeting`  
- `in_name`

There are three simple test cases that are published:  
- `EnglishCase`  
- `FrenchCase`  
- `SpanishCase`  

## GitHub Actions Workflows

### Environment Setup

In these examples, **Orchestrator Authentication** is handled with [External Applications](https://docs.uipath.com/automation-cloud/docs/managing-external-applications). 

[UiPath CLI](https://www.myget.org/feed/uipath-dev/package/nuget/UiPath.CLI) is used for Pack and Deploy functionality.

A [GitHub-hosted runner](https://docs.github.com/en/actions/using-github-hosted-runners/about-github-hosted-runners) (windows-latest) is used to run the workflows.

The following **'Secrets' are required** in your GitHub repository Settings -> Secrets:

- **`TENANT_NAME`** - _Target Cloud Orchestrator Tenant_
- **`ACCOUNT_NAME`** - _Target Cloud Orchestrator Account Name_ 
- **`OAUTH_CLIENT_ID`** - _App ID of External Application_
- **`OAUTH_CLIENT_SECRET`** - _App Secret of External Application_
- **`OAUTH_CLIENT_SCOPES`** - _Required scopes granted to External Application_






### Build And Deploy (Process)

#### [UiPathBuildDeploy.yml](.github/workflows/UiPathBuildDeploy.yml)  

###### Required Oauth Scopes:     
  
- OR.BackgroundTasks   
- OR.Execution   
- OR.Folders   
- OR.Settings

###### Workflow Steps

- **Build process package** (`iupcli`)    
- **Deploy to cloud orchestrator** (`iupcli`)    


`UiPathBuildDeploy.yml` is run on a [GitHub-hosted runner](https://docs.github.com/en/actions/using-github-hosted-runners/about-github-hosted-runners) (windows-latest).



### Build, Deploy And Run (Tests)


####[UiPathBuildDeployRun-Tests.yml](.github/workflows/UiPathBuildDeployRun-Tests.yml)  

###### Required Oauth Scopes:     
- OR.Assets   
- OR.BackgroundTasks   
- OR.Execution   
- OR.Folders   
- OR.Folders.Read   
- OR.Jobs   
- OR.Machines   
- OR.Monitoring   
- OR.Robots   
- OR.Settings   
- OR.Settings.Read   
- OR.TestSetExecutions   
- OR.TestSets   
- OR.Users
  
###### Workflow Steps

- **Build test package** (`iupcli`)  
- **Deploy to cloud orchestrator** (`iupcli`)    
- **Create test set** (`powershell`)
    - Get Access Token
    - Get Folder Id
    - Get Release
    - Get Test Case Definitions
    - Create test Set
    - Execute Test Set  

