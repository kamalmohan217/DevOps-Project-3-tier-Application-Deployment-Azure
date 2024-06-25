# DevOps-Project-3-tier-Application-Deployment-Azure
![image](https://github.com/kamalmohan217/DevOps-Project-3-tier-Application-Deployment-Azure/assets/128888356/56176858-c770-4d06-8297-2553ca6e03d6)
<br><br/>
For your reference the Source Code for this project is present in the GitHub Repository https://github.com/kamalmohan217/TWSThreeTierAppChallenge.git inside the directory Application-Code. However for the current project I have used Azure Repos into which the source code is present. as shown in the screenshot below.
![image](https://github.com/kamalmohan217/DevOps-Project-3-tier-Application-Deployment-Azure/assets/128888356/129bd84c-bb05-411b-bf30-22e006313736)
<br><br/>
1. This is a three tier application (of Things-to-Do App) in which frontend or presentation layer is React Js code which is present in the directory Application-Code/frontend in the GitHub Repo https://github.com/kamalmohan217/TWSThreeTierAppChallenge.git. To deploy React Js code I have created a Pipeline using Azure DevOps.
2. The Backend or Application layer is Node Js code which present in the directory Application-Code/backend in the GitHub Repo https://github.com/kamalmohan217/TWSThreeTierAppChallenge.git. To deploy Node Js code I have created a Pipeline using Azure DevOps.
3. For Database or Data layer MongoDB has been used. To deploy MongoDB I have created a Pipeline using Azure DevOps.
4. To Deploy the three Pipelines I have used Helm and helm chart. These helm charts are present in the GitHub Repo https://github.com/kamalmohan217/helm-repo-for-ArgoCD-three-tier-app-backend.git, https://github.com/kamalmohan217/helm-repo-for-ArgoCD-three-tier-app-frontend.git and https://github.com/kamalmohan217/helm-repo-for-ArgoCD-three-tier-app-database.git. In the current project I have clonned the helm chart from above mentioned repositories inside the home directory of user which is /home/demo.
<br><br/>
As discussed above there are three Pipelines using which ReactJs code, NodeJs code and MongoDB have been deployed. which is also shown in the Architechture diagram above. The azure-pipelines.yaml for ReactJs Code, NodeJs Code and MongoDB is present inside the directory azure-pipelines in this Repository. Before Running Jenkins Job for MongoDB create the password, pv (persistent volume) and pvc (persistent volume claim). To do so run the command kubectl apply -f pv.yaml, kubectl apply -f pvc.yaml and kubectl apply -f secrets.yaml. The password for MongoDB is encrypted with base64. 
<br><br/>
```
Encryption with Base64
==================================
echo "admin"|base64 -----------> Encrypt the username
ehco "password123"|base64  --------------> Encrypt the password


Decryption with Base64
==================================
echo "YWRtaW4="|base64 --decode
echo "cGFzc3dvcmQxMjM="|base64 --decode
```
The screenshot for SonarQube Analysis is shown below.
![image](https://github.com/kamalmohan217/DevOps-Project-3-tier-Application-Deployment-Azure/assets/128888356/9809fc4c-54b0-4188-ba50-966de90b78f6)
<br><br/>
To keep the Docker Images for frontend and backend I have created two container registries with the name of akscontainer24registry1 and akscontainer24registry2 respectively in Azure Container Registries (ACR) as shown in the screenshot below.
![image](https://github.com/kamalmohan217/DevOps-Project-3-tier-Application-Deployment-Azure/assets/128888356/1164e77e-2ec0-45ee-8b38-912dc657145c)
After Successfully Running the three Jenkins Job (successfully deployment of the three-tier Application) create the URL for the application using the file ingress-rule.yaml present inside the directory ingress-rule-pv-pvc-mongodbsecret with the command kubectl apply -f ingress-rule.yaml. Create a record set for the URL inside the hosted zone as shown in the screenshot below.
![image](https://github.com/kamalmohan217/DevOps-Project-3-tier-Application-Deployment-Azure/assets/128888356/4789f464-a7ae-43ba-aff2-92e1d4f38ce7)
<br><br/>
Using the created URL backend.singhritesh85.com access the application as shown in the screenshot below.
![image](https://github.com/kamalmohan217/DevOps-Project-3-tier-Application-Deployment-Azure/assets/128888356/ba049ecc-0e36-4a02-ab8c-a9a08469f9e0)
![image](https://github.com/kamalmohan217/DevOps-Project-3-tier-Application-Deployment-Azure/assets/128888356/f3e9fda1-3300-4d11-ac4f-5f228b59f6d4)
<br><br/>
After Successful deployment we can see the Applications using command line as shown in the screenshot below.
![image](https://github.com/kamalmohan217/DevOps-Project-3-tier-Application-Deployment-Azure/assets/128888356/e6f9caa8-c2b2-4176-aa2b-91c1cbbba9af)

<br><br/>
The Service Connection is created as shown in the screenshot below.
![image](https://github.com/kamalmohan217/DevOps-Project-3-tier-Application-Deployment-Azure/assets/128888356/eb91cf5b-c52e-456a-b457-6c3ee33988d7)
<br><br/>
The three pipelines in Azure DevOps is as shown in the screenshot below.
![image](https://github.com/kamalmohan217/DevOps-Project-3-tier-Application-Deployment-Azure/assets/128888356/509d8240-a3fd-426d-9ec3-1cad208bd707)
```
The frontend-auth and backend-auth secrets for kubernetes can be created using the command below

kubectl create secret docker-registry frontend-auth --docker-server=https://akscontainer24registry2.azurecr.io --docker-username=akscontainer24registry2 --docker-password=XXXXXXXXXXXXXXXXXXXXXXXXXXXOJ7eXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXFyh6 -n three-tier


kubectl create secret docker-registry backend-auth --docker-server=https://akscontainer24registry1.azurecr.io --docker-username=akscontainer24registry1 --docker-password=XXXXXXXXXXXXXXXXXXXXXXXXXXXX4rHeWXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX1skn -n three-tier
```
<br><br/>
<br><br/>
<br><br/>
<br><br/>
<br><br/>
<br><br/>
```
source Code:-  https://github.com/kamalmohan217/TWSThreeTierAppChallenge.git
```
<br><br/>
<br><br/>
<br><br/>
<br><br/>
<br><br/>
<br><br/>
```
Reference:-   https://github.com/LondheShubham153/TWSThreeTierAppChallenge.git
```
