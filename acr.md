## Create Azure Container Registry

>Explore contents of acrDeploy & acrDeploy.param.json in your favourite editor. Edit parameter values in acrDeploy.param.json as needed.

**Setup deployment variables for ACR:**\
PowerShell:

    $resourceDeploymentName = 'demoacrdeploy'
    # Change templatePath as per your environment
    $templatePath = $env:SystemDrive + '\' + 'users' + '\' + 'demok8s'
    $templateFile = 'acrDeploy.json'
    $templateParameterFile = 'acrDeploy.param.json'
    $template = $templatePath + '\' + $templateFile
    $templateParameter = $templatePath + '\' + $templateParameterFile

Bash:

    resourceDeploymentName='demoacrdeploy'
    # Change templatePath as per your environment
    templatePath=$HOME/demok8s
    templateFile=acrDeploy.json
    templateParameterFile=acrDeploy.param.json
    template=$templatePath/$templateFile
    templateParameter=$templatePath/$templateParameterFile

**Create Azure Container Registry:**\
PowerShell:

    New-AzResourceGroupDeployment `
     -Name $resourceDeploymentName `
     -ResourceGroupName $resourceGroupName `
     -TemplateFile $template `
     -TemplateParameterFile $templateParameter `
     -Verbose -Force

Bash:

    ```az group deployment create \
    --name $resourceDeploymentName \
    --resource-group $resourceGroupName \
    --template-file $template \
    --parameters @$templateParameter \
    --no-wait ```

Continue to [Create a Kubernetes cluster in Azure](aks.md) \
Back to [Configure your environment](envconfigure.md) or to [Home](README.md)