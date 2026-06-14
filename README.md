<img width="905" height="292" alt="image" src="https://github.com/user-attachments/assets/f0d8c49e-7d1e-4c39-bfc4-451852f4ab41" />

Code compile -> using maven

Static code analysis - using sonarqube

Code build -> using maven

Docker build -> using docker

Push image to dockerhub 

Deploy to K8s

used **t2 large** instance for this activity

**Plugins Installed** - Pipeline: Stage View, Eclipse Temurin installer, Maven Integration, SonarQube Scanner, Docker commons, Docker Pipeline, Docker API, Docker, Kubernetes cli 

---

## Install jenkins and plugins


[follow this doc](https://github.com/gashok13193/DevOps-Docs/blob/main/Jenkins/Jenkins%20Setup.md)

- Below is the latest version

<img width="1830" height="1002" alt="image" src="https://github.com/user-attachments/assets/35690ef8-7827-498c-b5b1-10eaca61b4fb" />


- Allow the port for jenkins `8080`

- Test the git checkout functionality by creating a pipeline

   pipeline name: `CICD` --> Pipeline Script

- Generate the pipeline script by going to `pipeline syntax`

<img width="1918" height="977" alt="image" src="https://github.com/user-attachments/assets/d51ebd0d-c12a-4dd4-a89e-b5f7937206d0" />

<img width="1908" height="883" alt="image" src="https://github.com/user-attachments/assets/a9fadc75-1168-4a5b-80fb-d0081b28951d" />


- Click the `Build Now` and install the plugin `stage view` so that we can able to view it properly.

---
## Install the Maven

[follow this doc](https://github.com/gashok13193/DevOps-Docs/blob/main/MAVEN/maven.md#installing-maven-on-linuxubuntu)

- Configure the Maven with jenkins, install maven and temurin plugins.

- Jenkins --> tools --> Maven

<img width="1317" height="497" alt="image" src="https://github.com/user-attachments/assets/dc0a285f-546d-4dee-9b0d-e7af19c4ad96" />

- Jenkins --> tools --> JDK Installations

<img width="1363" height="460" alt="image" src="https://github.com/user-attachments/assets/47d04e1c-99ce-48c2-9920-a807b1eb5379" />

<img width="1526" height="425" alt="image" src="https://github.com/user-attachments/assets/e1d98d7e-6672-492a-afe4-c323ba012e62" />

- Save it

---
## Configure the tools in jenkins pipeline

<img width="585" height="126" alt="image" src="https://github.com/user-attachments/assets/ac5b754f-fb6d-4371-bf8e-83448004e5bd" />

---
## Code compile using Maven

<img width="1487" height="665" alt="image" src="https://github.com/user-attachments/assets/66caa979-8b00-4660-8d63-dcefd01c001b" />

- Now build and test it

<img width="1566" height="576" alt="image" src="https://github.com/user-attachments/assets/500a4605-3d37-4acf-b09a-fa7fcf1f6be0" />

---

## Install the SonarQube and do Static code analysis

[follow-this-doc-go-to-package-step](https://github.com/gashok13193/DevOps-Docs/blob/main/SonarQube/SonarQube.md)

```bash
sudo apt install unzip
./sonar.sh start
```

- allow the port `9000` for sonarqube.


```bash
username: admin
password: admin
```

- Configure the sonarqube

<img width="1073" height="676" alt="image" src="https://github.com/user-attachments/assets/c2ce04b3-f9b7-492e-a136-49b1527dd340" />

<img width="845" height="468" alt="image" src="https://github.com/user-attachments/assets/e308559c-d6bc-4207-860b-137b368e6ac3" />

- Select with jenkins

<img width="1363" height="393" alt="image" src="https://github.com/user-attachments/assets/851d55fa-624a-4189-880c-ae57b95b9d41" />

- Select github

<img width="702" height="291" alt="image" src="https://github.com/user-attachments/assets/cac15733-9e0b-4283-b66e-b6acc7453bec" />

- configure analysis

<img width="333" height="178" alt="image" src="https://github.com/user-attachments/assets/ed98b6f7-6717-45c5-b9a0-5d50a628a491" />


<img width="577" height="270" alt="image" src="https://github.com/user-attachments/assets/a37dbee8-f2ff-4425-8aaa-055e8f0b8072" />

- click continue ..., select maven and finish tutorial

- Click security --> generate token

<img width="1403" height="467" alt="image" src="https://github.com/user-attachments/assets/93dff6c6-a35c-432e-8f1b-fb78e11b23f2" />

- Copy the token and keep it. It is used to authenticate jenkins
  
<img width="777" height="212" alt="image" src="https://github.com/user-attachments/assets/097b46b2-2023-4d39-b847-9ebcb17bd33f" />

- Install the plugin `sonarQube scanner`.

- Create the creds for sonarqube. Manage Jenkins --> Credentials, in secret text we need to paste the token

<img width="1533" height="642" alt="image" src="https://github.com/user-attachments/assets/14032d4a-324c-43f5-be41-99e20fa7fa7a" />

<img width="1577" height="397" alt="image" src="https://github.com/user-attachments/assets/149fc8cc-f6c0-45ed-9b39-11d31493596e" />


- Configure the tools for sonarqube

<img width="1440" height="407" alt="image" src="https://github.com/user-attachments/assets/5467b968-ef8a-4297-bdd0-4b1e830068a3" />

<img width="1217" height="617" alt="image" src="https://github.com/user-attachments/assets/f67c1630-1739-48c2-b547-cf77d983051b" />

- Add the server for sonarqube

<img width="1438" height="630" alt="image" src="https://github.com/user-attachments/assets/e018b7e2-adf8-44a5-bfbd-3979b64de5f4" />

- Now configure the pipeline for sonarqube, but in tools section we can't able to add sonarqube. so we need to add it as `env` option.

<img width="701" height="227" alt="image" src="https://github.com/user-attachments/assets/70dd5330-e75b-42e2-983d-06e7c147e7cc" />

<img width="1012" height="240" alt="image" src="https://github.com/user-attachments/assets/c3eb9b6d-c9fa-4b93-a6d0-18bc9aed6d5b" />

- Now build the pipeline , it should get successful

<img width="1577" height="647" alt="image" src="https://github.com/user-attachments/assets/eff61124-68a3-4ac3-a3c6-8ddedbc10d84" />

<img width="1550" height="446" alt="image" src="https://github.com/user-attachments/assets/64b23c13-780e-40aa-97cc-d866b7cff6cc" />

---

## Code Build using Maven


<img width="985" height="186" alt="image" src="https://github.com/user-attachments/assets/6bf78413-7f93-4f12-82bd-eeca526e91d2" />

- Once the codebuild completes successfully, we can see the files created under workspaces directory.

<img width="1567" height="625" alt="image" src="https://github.com/user-attachments/assets/852cd4a0-d151-4ea1-aa31-45f9574f63aa" />

- we can see the `.jar` file.

<img width="1703" height="586" alt="image" src="https://github.com/user-attachments/assets/7b84d93d-d494-4ba4-87e9-d695dd35fa30" />


---

## Install the docker

[follow this doc for installation](https://github.com/SeshadriRC/DevOps-Docs/blob/main/Docker/Docker.md)

- plugins install

<img width="1150" height="587" alt="image" src="https://github.com/user-attachments/assets/482e097a-fda2-42df-b5a7-06503e3de49d" />

- configure the tools for docker

<img width="1533" height="561" alt="image" src="https://github.com/user-attachments/assets/1c6d8565-f3cd-4f2e-ae67-91e010015461" />

- configure the creds for docker

<img width="1571" height="648" alt="image" src="https://github.com/user-attachments/assets/ce1e9add-069d-4bb1-a635-89f6218cc589" />

- pipeline syntax

<img width="1602" height="707" alt="image" src="https://github.com/user-attachments/assets/4700fed2-557f-4358-ae1b-7830f37a6d51" />

<img width="957" height="207" alt="image" src="https://github.com/user-attachments/assets/1c212fb4-04e5-44a0-ab61-ad7180ae27da" />

- Now build the pipeline and check the docker images

<img width="1571" height="551" alt="image" src="https://github.com/user-attachments/assets/9b6d187e-9a49-4dd4-a183-416fef6fd489" />

- Push the docker image to docker hub

<img width="1106" height="430" alt="image" src="https://github.com/user-attachments/assets/5ed916eb-67ed-404b-b0cb-e1007508f946" />


---

## Deploy to the kubernetes

```
sudo chmod +x kubeadm.sh
```

[follow the doc to install](https://github.com/SeshadriRC/DevOps-Docs/blob/main/Kubernetes/kubeadm_jenkins_maven_docker.sh)


- Install the plugin `kubernetes cli`
- using the config file , we can login to the cluster. from `apiversion upto last`.
- upload the text file.

<img width="1517" height="635" alt="image" src="https://github.com/user-attachments/assets/aecb4bd5-0081-481b-8b5b-e1208ab132b0" />

- pipeline syntax

<img width="1545" height="546" alt="image" src="https://github.com/user-attachments/assets/ed6c0661-d2e6-4253-ba91-29116d423da9" />

- Only `credentialID` is required, remove all other things.

<img width="1053" height="265" alt="image" src="https://github.com/user-attachments/assets/fbe7a1f4-1614-48b1-8c96-a9576a451d77" />

<img width="1600" height="467" alt="image" src="https://github.com/user-attachments/assets/f1e82bba-f6fa-47ad-9860-91faf3fa166f" />

