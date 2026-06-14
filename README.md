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

[follow this official doc](https://www.jenkins.io/doc/book/installing/linux/#debianubuntu)


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

<img width="1080" height="197" alt="image" src="https://github.com/user-attachments/assets/cc750c00-dc93-4be7-bf39-6c970ba81365" />


```bash
sudo apt install maven
```

- Configure the Maven with jenkins, install maven and temurin plugins.

  <img width="1917" height="668" alt="image" src="https://github.com/user-attachments/assets/854999f3-2925-4449-9cf6-56606b5f54e5" />


- Jenkins --> tools --> Maven

<img width="1917" height="953" alt="image" src="https://github.com/user-attachments/assets/f9c61eb2-a858-4933-aa84-c90b25da3724" />

<img width="1062" height="192" alt="image" src="https://github.com/user-attachments/assets/c7cd2198-f1a5-4127-a259-5f5721e54f63" />


- Jenkins --> tools --> JDK Installations

<img width="1915" height="775" alt="image" src="https://github.com/user-attachments/assets/1cc80f02-a28e-4297-82c9-245c6034ac4b" />


- Save it

---
## Configure the tools in jenkins pipeline

<img width="1918" height="863" alt="image" src="https://github.com/user-attachments/assets/34a56d34-2af7-4bea-9270-1d97327e2221" />

---
## Code compile using Maven

<img width="1282" height="373" alt="image" src="https://github.com/user-attachments/assets/6e63245b-ce58-4f1a-aeca-c83b70e7734b" />


- Now build and test it

<img width="1918" height="581" alt="image" src="https://github.com/user-attachments/assets/e96380dd-44c8-4408-8a74-1b13f92446fc" />

---

## Install the SonarQube and do Static code analysis

[follow-this-doc-go-to-package-step](https://github.com/gashok13193/DevOps-Docs/blob/main/SonarQube/SonarQube.md)

```bash
curl -s https://www.sonarsource.com/products/sonarqube/downloads/historical-downloads/ \
| grep -oE 'sonarqube-[0-9.]+\.zip'

wget --spider https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-10.7.0.96327.zip

wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-10.7.0.96327.zip

sudo apt install unzip

unzip sonarqube-10.7.0.96327.zip

./sonar.sh start
```

- allow the port `9000` for sonarqube. i faced issue in laptop for port `9000` so i used `3456`. in mobile `9000` is worked, not sure why


```bash
username: admin
password: admin
new: sesha123
```

- Configure the sonarqube

<img width="1918" height="880" alt="image" src="https://github.com/user-attachments/assets/89fafa37-fd5f-4698-89c6-7c64fbe6b7d6" />

<img width="1818" height="837" alt="image" src="https://github.com/user-attachments/assets/5db7a84e-ee44-4ba0-ae53-ae791eb3ab3b" />

- Select with jenkins

<img width="1917" height="737" alt="image" src="https://github.com/user-attachments/assets/3b5694f8-39c5-4570-b64e-5aee16539680" />


- Select github

<img width="1887" height="470" alt="image" src="https://github.com/user-attachments/assets/41b1bd64-e16a-4329-bd11-e331d7eb9a04" />

- configure analysis

<img width="1918" height="482" alt="image" src="https://github.com/user-attachments/assets/907d5aea-934c-4098-8b7e-7db91b1ed17b" />


- click continue ..., select maven and finish tutorial

<img width="1918" height="707" alt="image" src="https://github.com/user-attachments/assets/60c4a70c-b397-470d-a0a9-4c7361e53e8d" />

<img width="1918" height="792" alt="image" src="https://github.com/user-attachments/assets/229a079b-0c7d-4aaa-b38f-47ecc6add1d6" />

<img width="1918" height="726" alt="image" src="https://github.com/user-attachments/assets/879b37ef-822f-4fa3-8ed2-88eb75d42aef" />


- Click security --> generate token

<img width="1403" height="467" alt="image" src="https://github.com/user-attachments/assets/93dff6c6-a35c-432e-8f1b-fb78e11b23f2" />

- Copy the token and keep it. It is used to authenticate jenkins
  
<img width="1917" height="822" alt="image" src="https://github.com/user-attachments/assets/e916eef3-88be-466e-a303-a0d4bf8458e7" />


- Install the plugin `sonarQube scanner`.

  <img width="1918" height="512" alt="image" src="https://github.com/user-attachments/assets/b6fa1f15-1891-46d2-9dd8-bcccb98d337f" />


- Create the creds for sonarqube. Manage Jenkins --> Credentials, in secret text we need to paste the token

<img width="1918" height="778" alt="image" src="https://github.com/user-attachments/assets/2906915e-a797-40d8-9494-c1650dfea1c8" />

<img width="1911" height="327" alt="image" src="https://github.com/user-attachments/assets/40c22297-bb71-4bce-8a69-22c36add06da" />


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

