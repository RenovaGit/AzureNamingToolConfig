# AzureNamingToolConfig
Renova specific settings and config for [Azure Naming Tool](https://github.com/mspnp/AzureNamingTool)

*"The Azure Naming Tool was created to help administrators define and manage their naming conventions, while providing a simple interface for users to generate a compliant name."*


## Pre requisite
The naming tool supports multiple installation alternatives and can also be used as an integrated part in build pipelines.

We'll start with the simple and decoupled approach - just a stand alone application providing web based assistance in getting the naming of resources right.

This description is based on the assumption that every user will run Azure Naming Tool locally and on a per need basis.

**We use Docker for this**

1. Get a Docker environment installed on your workstation.
2. Head over to Azure Naming Tool [Run as a Docker Image](https://github.com/mspnp/AzureNamingTool/wiki/Run-as-a-Docker-Image). Follow the instruction up to and including the `docker build...`. Do **not execute** `docker run...`

You now have an Azure Naming Tool container image installed in your local Docker registry.

## How to
Azure Naming Tool stores all setting in a bunch of JSON files. This repo is where we track and mange these settings. When starting the Azure Naming Tool docker image we'll simple mount this repository content into the image.

1. Clone this repo to your local file system. You'll end up with a folder named AzureNamingToolConfig filled with json files. Note the full path to AzureNamingToolConfig.

2. Run `docker run -d -p 8081:80 --mount type=bind,source="<full path to AzureNamingToolConfig>",target=/app/settings azurenamingtool:latest`

3. Open browser: `http://localhost:8081`

4. The admin pwd is `Administrator1`

5. If you alter the configuration - **remember to commit this repo** to preserve the changes.
