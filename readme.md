# WINAE: a Windows based containerized Adobe After Effects renderer

---

### Related Blog

[Cloud Rendering Adobe After Effects Video with Windows Docker Container](https://mohohan.com/393)

### Prerequisite


| Item                | Detail                                                                                                                                                   |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Host Machine / OS   | Hardware configuration requires at least a 4-core processor and 8GB of memory. The operating system must be Windows 10/11 and a 64-bit operating system. |
| Software            | [Installed Docker Desktop Windows](https://docs.docker.com/desktop/install/windows-install/)                                                             |
| Software (Optional) | Installed Adobe After Effects 2022 Must have a genuine license                                                                                           |
| Software            | [Adobe After Effects Installer Package](https://adminconsole.adobe.com) Must have a genuine license                                                      |
| Software (Optional) | Rowbyte Plexus Plugin Must have a genuine license                                                                                                        |
| Cloud Platform      | Azure account with a subscription ([Sign up](https://signup.azure.com/signup) if you don't have it)                                                      |
| Github              | Github account ([Sign up](https://github.com/signup) if you don't have it)                                                                               |

---

### Installation


| Step | Detail                                                                                                                                                                                                                                                                                                |
| ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1    | [Fork this repo](https://github.com/theringe/winae/fork)                                                                                                                                                                                                                                              |
|      | ![Step 1-01](docs/images/1-01.png "Step 1-01")                                                                                                                                                                                                                                                        |
|      | ![Step 1-02](docs/images/1-02.png "Step 1-02")                                                                                                                                                                                                                                                        |
| 2    | [![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Ftheringe%2Fwinae%2Fmaster%2Fwinae.json)                                                                                                    |
| 2-01 | Create a new "Resource Group" by specifying a name (e.g., winae-mytest-rg)                                                                                                                                                                                                                            |
|      | ![Step 2-01](docs/images/2-01.png "Step 2-01")                                                                                                                                                                                                                                                        |
| 2-02 | Select a proper "Region" nearby your workplace, Keep "Resource Prefix" and "Encryption Key" as default value                                                                                                                                                                                          |
|      | ![Step 2-02](docs/images/2-02.png "Step 2-02")                                                                                                                                                                                                                                                        |
| 2-03 | Click "Create"                                                                                                                                                                                                                                                                                        |
|      | ![Step 2-03](docs/images/2-03.png "Step 2-03")                                                                                                                                                                                                                                                        |
| 2-04 | Wait for Azure around 10-20 minutes to allocate the related resources                                                                                                                                                                                                                                 |
|      | ![Step 2-04](docs/images/2-04.png "Step 2-04")                                                                                                                                                                                                                                                        |
| 2-05 | Click "Go to resource group" once the deployment has been done                                                                                                                                                                                                                                        |
|      | ![Step 2-05](docs/images/2-05.png "Step 2-05")                                                                                                                                                                                                                                                        |
| 2-06 | In the resource group, click the "Deployment Script" resource                                                                                                                                                                                                                                         |
|      | ![Step 2-06](docs/images/2-06.png "Step 2-06")                                                                                                                                                                                                                                                        |
| 2-07 | In the "Overview" section from "Deployment Script" resource, copy all the information from "Logs" for further use (in How to use: 1-??), then close this resource and go back to resource group                                                                                                                   |
|      | ![Step 2-07](docs/images/2-07.png "Step 2-07")                                                                                                                                                                                                                                                        |
| 2-08 | Back to resource group, click the "Function App" resource                                                                                                                                                                                                                                             |
|      | ![Step 2-08](docs/images/2-08.png "Step 2-08")                                                                                                                                                                                                                                                        |
| 2-09 | In the "Deployment Center" section from "Function App" resource, select "GitHub" as the source                                                                                                                                                                                                        |
|      | ![Step 2-09](docs/images/2-09.png "Step 2-09")                                                                                                                                                                                                                                                        |
| 2-10 | Then click "Authorize"                                                                                                                                                                                                                                                                                |
|      | ![Step 2-10](docs/images/2-10.png "Step 2-10")                                                                                                                                                                                                                                                        |
| 2-11 | You will be redirected to github.com and select your GitHub account to login                                                                                                                                                                                                                          |
|      | ![Step 2-11](docs/images/2-11.png "Step 2-11")                                                                                                                                                                                                                                                        |
| 2-12 | Then authorize Azure App Service by click the button                                                                                                                                                                                                                                                  |
|      | ![Step 2-12](docs/images/2-12.png "Step 2-12")                                                                                                                                                                                                                                                        |
| 2-13 | Back to Azure Portal, now your GitHub account has been associated with your Azure account, select your GitHub account as the "Organization", "winae" as the "Repository", and "master" as the "Branch". Then click "save"                                                                             |
|      | ![Step 2-13](docs/images/2-13.png "Step 2-13")                                                                                                                                                                                                                                                        |
| 2-14 | You are now deploying the control panel of WINAE to Function App, wait for Azure around 5-10 minutes to publish the code on server, you can got to "Actions" in your forked Github repo to see the latest status, once finished, you can see some Functions in the "Overview" section, click "index"  |
|      | ![Step 2-14](docs/images/2-14.png "Step 2-14")                                                                                                                                                                                                                                                        |
| 2-15 | In "Code + Test" section, click "Get function URL" and then copy the URL for further use (in 2-28), it is the URL of the WINAE control panel, finally go back to the "Function App" resource                                                                                                          |
|      | ![Step 2-15](docs/images/2-15.png "Step 2-15")                                                                                                                                                                                                                                                        |
| 2-16 | Again in the "Function App" resource, go to "Authentication" section and click "Add identity provider"                                                                                                                                                                                                |
|      | ![Step 2-16](docs/images/2-16.png "Step 2-16")                                                                                                                                                                                                                                                        |
| 2-17 | Select "Microsoft" as "Identity provider" and click "Add"                                                                                                                                                                                                                                             |
|      | ![Step 2-17](docs/images/2-17.png "Step 2-17")                                                                                                                                                                                                                                                        |
| 2-18 | Wait for Azure around 1-2 minutes to issue the app registration, and click the target "identity provider" when ready                                                                                                                                                                                  |
|      | ![Step 2-18](docs/images/2-18.png "Step 2-18")                                                                                                                                                                                                                                                        |
| 2-19 | This is the page of the new created "App registration". In "Overview" section, copy "Application ID" and "Tenant ID" for further use (in 2-20), then go back to "Function App" resource                                                                                                               |
|      | ![Step 2-19](docs/images/2-19.png "Step 2-19")                                                                                                                                                                                                                                                        |
| 2-20 | Again in the "Function App" resource, go to "Environment variables" section, create 2 variables: set "MICROSOFT_PROVIDER_AUTHENTICATION_APPID" and "MICROSOFT_PROVIDER_AUTHENTICATION_TENANTID" as the related value you have copied from 2-21, then click "Apply" and go back to resource group page |
|      | ![Step 2-20](docs/images/2-20.png "Step 2-20")                                                                                                                                                                                                                                                        |
| 2-21 | Again in the resource group, click the "Storage Account" resource                                                                                                                                                                                                                                     |
|      | ![Step 2-21](docs/images/2-21.png "Step 2-21")                                                                                                                                                                                                                                                        |
| 2-22 | In the "Storage Account" resource, go to "File shares" section and click "winae-file"                                                                                                                                                                                                                 |
|      | ![Step 2-22](docs/images/2-22.png "Step 2-22")                                                                                                                                                                                                                                                        |
| 2-23 | In "Overview" page, click "Connect", select "A" as "Drive Letter", click "Show Script", then copy the script for further use (in How to use: 1-??), finally close this page                                                                                                                                       |
|      | ![Step 2-23](docs/images/2-23.png "Step 2-23")                                                                                                                                                                                                                                                        |
| 2-24 | Go back to resource group page                                                                                                                                                                                                                                                                        |
|      | ![Step 2-24](docs/images/2-24.png "Step 2-24")                                                                                                                                                                                                                                                        |
| 2-25 | Again in the resource group, click the "Access Control (IAM)" section, click "Role Assignments", click "Add" and select "Add role assignment"                                                                                                                                                         |
|      | ![Step 2-25](docs/images/2-25.png "Step 2-25")                                                                                                                                                                                                                                                        |
| 2-26 | In role assignment page, click "Privileged administratior roles", select "Contributor", and click "Next"                                                                                                                                                                                              |
|      | ![Step 2-26](docs/images/2-26.png "Step 2-26")                                                                                                                                                                                                                                                        |
| 2-27 | In this page, click "Select members", and search for "winae", choose the app registration which be created from 2-21, finally click "Next", "Select" and "Review + assign"                                                                                                                            |
|      | ![Step 2-27](docs/images/2-27.png "Step 2-27")                                                                                                                                                                                                                                                        |
| 2-28 | Open a browser tab, paste the URL copied (from 2-15) and proceed with the installation guide on that page (Control Panel)                                                                                                                                                                             |
|      | [**Once all the installation steps on the control panel page have been completed, return to step 5 on this page to continue**]                                                                                                                                                                        |
| 5    |                                                                                                                                                                                                                                                                                                       |
|      |                                                                                                                                                                                                                                                                                                       |
|      |                                                                                                                                                                                                                                                                                                       |
|      |                                                                                                                                                                                                                                                                                                       |
|      |                                                                                                                                                                                                                                                                                                       |
|      |                                                                                                                                                                                                                                                                                                       |
|      |                                                                                                                                                                                                                                                                                                       |
|      |                                                                                                                                                                                                                                                                                                       |
|      |                                                                                                                                                                                                                                                                                                       |
|      |                                                                                                                                                                                                                                                                                                       |

### How To Use
