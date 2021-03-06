
## Overview

## Installation

* requirement xl-deploy-server 9.0.0+
* Copy the latest JAR file from the [releases page](https://github.com/xebialabs-community/xld-helm-plugin/releases) into the `XL_DEPLOY_SERVER/plugins` directory.
* Restart the XL Deploy server.

* xl-deploy-9.6-server with the following plugings
  * [xld-terraform-enterprise-plugin](https://github.com/xebialabs-community/xld-terraform-enterprise-plugin)
  * [xld-ansible-step-plugin](https://github.com/xebialabs-community/xld-ansible-step-plugin)

* xl-release-9.6-server with the following plugings:
  * xlr-servicenow-plugin
  * [overtherepy jar file](https://github.com/xebialabs-community/overthere-pylib/releases/download/v0.0.4/overtherepy-0.0.4.jar) into the `XL_RELEASAE_SERVER/plugins/__local__` directory.
  * xlr-devops-as-code-plugin from [releases page](https://github.com/xebialabs-community/xlr-devops-as-code-plugin/releases) into the `XL_RELEASE_SERVER/plugins/__local__` directory.
  * cp servicenow directory to ${XL_RELEASE_HOME}/ext

## XLDeploy Configuration

store you azure credentials into ~/.xebialabs/azure.secrets.xlvals (you can use dummy values)
````
cat ~/.xebialabs/azure.secrets.xlvals
subscriptionId: azerty-a628-43e2-456f-1f9ea1b3ece3
tenantId: qwerty-5162-f14d-ab57-a0235a2385e0
clientId: benoit-820a-404b-efed-4cf7c0a99796
clientKey: p/v-Mmoussauda0yry3W7L3OB
````

store you AWS credentials into ~/.xebialabs/aws.secrets.xlvals (you can use dummy values)
```
$cp  ~/.aws/credentials ~/.xebialabs/aws.secrets.xlvals
```

Apply the XLDeploy configuration to define the configuration items
```
$export XL_VALUE_tfe_token="6SPlj2J5LMuw.atlasv1.Lm.........GWrnkSUZy1oCg"
$xl apply --config.yaml -f cloud/xebialabs.yaml 
$./xlw --config config.yaml apply -f xebialabs/xebialabs-cloud.yaml
```

To spin up the 2 virtual machines in AWS/EC2
```
$./xld.sh Applications/cloud-infrastructure/2.0.1 Environments/petportal/petportal.dev
```



