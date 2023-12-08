# GitHub_WorkFlows
CICD - Continuous Integration Continuous Delivery
![image](https://github.com/himanshunimje1/GitHub_WorkFlows/assets/33219247/5a988e67-208a-48fc-80b9-ae4799f2d0ce)

1. Development WorkFlow 



Org Development Model Vs Package Development Model:

This guide helps Salesforce developers who are new to Visual Studio Code go from zero to a deployed app using Salesforce Extensions for VS Code and Salesforce CLI.

Part 1: Choosing a Development Model
There are two types of developer processes or models supported in Salesforce Extensions for VS Code and Salesforce CLI. These models are explained below. Each model offers pros and cons and is fully supported.

Package Development Model
The package development model allows you to create self-contained applications or libraries that are deployed to your org as a single package. These packages are typically developed against source-tracked orgs called scratch orgs. This development model is geared toward a more modern type of software development process that uses org source tracking, source control, and continuous integration and deployment.

If you are starting a new project, we recommend that you consider the package development model. To start developing with this model in Visual Studio Code, see Package Development Model with VS Code. For details about the model, see the Package Development Model Trailhead module.

If you are developing against scratch orgs, use the command SFDX: Create Project (VS Code) or sfdx force:project:create (Salesforce CLI) to create your project. If you used another command, you might want to start over with that command.

When working with source-tracked orgs, use the commands SFDX: Push Source to Org (VS Code) or sfdx force:source:push (Salesforce CLI) and SFDX: Pull Source from Org (VS Code) or sfdx force:source:pull (Salesforce CLI). Do not use the Retrieve and Deploy commands with scratch orgs.

Org Development Model
The org development model allows you to connect directly to a non-source-tracked org (sandbox, Developer Edition (DE) org, Trailhead Playground, or even a production org) to retrieve and deploy code directly. This model is similar to the type of development you have done in the past using tools such as Force.com IDE or MavensMate.

To start developing with this model in Visual Studio Code, see Org Development Model with VS Code. For details about the model, see the Org Development Model Trailhead module.

If you are developing against non-source-tracked orgs, use the command SFDX: Create Project with Manifest (VS Code) or sfdx force:project:create --manifest (Salesforce CLI) to create your project. If you used another command, you might want to start over with this command to create a Salesforce DX project.

When working with non-source-tracked orgs, use the commands SFDX: Deploy Source to Org (VS Code) or sfdx force:source:deploy (Salesforce CLI) and SFDX: Retrieve Source from Org (VS Code) or sfdx force:source:retrieve (Salesforce CLI). The Push and Pull commands work only on orgs with source tracking (scratch orgs).

The sfdx-project.json File
The sfdx-project.json file contains useful configuration information for your project. See Salesforce DX Project Configuration in the Salesforce DX Developer Guide for details about this file.

The most important parts of this file for getting started are the sfdcLoginUrl and packageDirectories properties.

The sfdcLoginUrl specifies the default login URL to use when authorizing an org.

The packageDirectories filepath tells VS Code and Salesforce CLI where the metadata files for your project are stored. You need at least one package directory set in your file. The default setting is shown below. If you set the value of the packageDirectories property called path to force-app, by default your metadata goes in the force-app directory. If you want to change that directory to something like src, simply change the path value and make sure the directory you’re pointing to exists.

"packageDirectories" : [
    {
      "path": "force-app",
      "default": true
    }
]
Part 2: Working with Source
For details about developing against scratch orgs, see the Package Development Model module on Trailhead or Package Development Model with VS Code.

For details about developing against orgs that don’t have source tracking, see the Org Development Model module on Trailhead or Org Development Model with VS Code.

Part 3: Deploying to Production
Don’t deploy your code to production directly from Visual Studio Code. The deploy and retrieve commands do not support transactional operations, which means that a deployment can fail in a partial state. Also, the deploy and retrieve commands don’t run the tests needed for production deployments. The push and pull commands are disabled for orgs that don’t have source tracking, including production orgs.

Deploy your changes to production using packaging or by converting your source into metadata format and using the metadata deploy command.
