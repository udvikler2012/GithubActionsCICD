# GithubActionsCICD
Demo of CICD Workflow running on Github Actions


source: https://docs.microsoft.com/en-us/dotnet/architecture/devops-for-aspnet-developers/actions-index 

Environment is only available for public repositories.
Deployment slots are only available for Azure WebApps with Standard/Premium level

Demo of:
Build flow
Deploy to Azure apps using ServicePrincipal (stage swap not implemented as it requires production Azure subscription ($$$$)
Using Environments to deploy to PRE_PROD or PROD. (You can setup Environment Protection to set up manual approval of deploy)
Using secrets (global and for environment)
Using configuration replacement variables
setting up a security scan for security and quality warnings (show 


Takeaway:
Workflow is created as files in .github using github Actions.
   jobs: -> steps: -> - tasks  
  on: specifies triggers,
  runs-on: specifies the runner(agent)
  uses: specifies github action for a task
  run: specifies a commandline command
  with: specifies config details
  needs: specifies previous build step succesfully run.
Security workflow is added as another workflow running. Security configuration can be done in separate config file
Environment is used to control multiple deployments
Azure ServicePrincipal is created using azure cli or in Portal (App Registrations - remember to create client secret, and then setup assignment on webapp IAM settings.)

