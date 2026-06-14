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

- Below method not worked , so i ran this as a docker container
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

### another method

```bash
docker run -d --name sonarqube -p 3456:9000 sonarqube:lts-community
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

<img width="1918" height="860" alt="image" src="https://github.com/user-attachments/assets/d9c53158-1f87-486d-914e-594e47a88d2f" />


- Add the server for sonarqube

<img width="1915" height="867" alt="image" src="https://github.com/user-attachments/assets/7ace0c03-f8d6-4ef7-a5ac-1bac78fb57e3" />


- Now configure the pipeline for sonarqube, but in tools section we can't able to add sonarqube. so we need to add it as `env` option.

<img width="1907" height="517" alt="image" src="https://github.com/user-attachments/assets/fc769832-ccaa-47e9-aea7-01646ef5418d" />

<img width="1113" height="307" alt="image" src="https://github.com/user-attachments/assets/01000cc9-d662-466f-8d21-74fe3df06ca6" />


- Now build the pipeline , it should get successful

<img width="1831" height="521" alt="image" src="https://github.com/user-attachments/assets/875cf713-f9b8-4256-942b-019415cc5424" />

<img width="1918" height="563" alt="image" src="https://github.com/user-attachments/assets/2af937d2-79b7-4acd-a0eb-d65500628e15" />


---

## Code Build using Maven


<img width="1336" height="405" alt="image" src="https://github.com/user-attachments/assets/58f1b318-b699-478b-b894-49f897a77a7e" />


- Once the codebuild completes successfully, we can see the files created under workspaces directory.

<img width="1915" height="502" alt="image" src="https://github.com/user-attachments/assets/976ba7fa-bfbf-4f94-acd6-a560b1850408" />

- we can see the `.jar` file.

<img width="1917" height="576" alt="image" src="https://github.com/user-attachments/assets/5bd4af2f-c6fc-40d9-b7e3-bd4423818bc2" />


---

## Install the docker

[follow this doc for installation](https://github.com/SeshadriRC/DevOps-Docs/blob/main/Docker/Docker.md)
[official-doc](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)

```bash
# run below commands, post installation

sudo usermod -aG docker jenkins
sudo systemctl restart jenkins
sudo systemctl restart docker

```

- plugins install

<img width="1918" height="852" alt="image" src="https://github.com/user-attachments/assets/c909d318-588b-43f0-9ac4-dcbe9289d299" />

- configure the tools for docker, its not required as per chatgpt.

<img width="1906" height="843" alt="image" src="https://github.com/user-attachments/assets/a8f22d24-428d-443c-8408-3412184c8008" />


- configure the creds for docker. i copied PAT from dockerhub --> settings

<img width="1918" height="892" alt="image" src="https://github.com/user-attachments/assets/da199587-0207-455d-a1a0-324a4307f1f7" />

<img width="1913" height="437" alt="image" src="https://github.com/user-attachments/assets/3e4e3c62-e0ae-47a9-91cb-6e9c61846929" />

- pipeline syntax

    - By default it will take url as `docker.io`
      
<img width="1917" height="831" alt="image" src="https://github.com/user-attachments/assets/9b36d290-1078-458e-afd3-e76956f62aff" />


<img width="1423" height="412" alt="image" src="https://github.com/user-attachments/assets/256bc63e-5c86-4303-8557-16f6235ea69b" />


- Now build the pipeline and check the docker images

<img width="1913" height="590" alt="image" src="https://github.com/user-attachments/assets/e9111f5e-bc3f-4a02-856b-1c9c9dcb06e6" />


<img width="1918" height="580" alt="image" src="https://github.com/user-attachments/assets/9e7dde2e-284c-461b-a790-f0c3d1cab4b0" />

- Push the docker image to docker hub

<img width="1877" height="641" alt="image" src="https://github.com/user-attachments/assets/a51ca10e-b6ee-45ca-9a3f-c9ccb9c2c605" />

<img width="1918" height="822" alt="image" src="https://github.com/user-attachments/assets/c7e3ed4f-73be-4987-a9f7-7614c571e56e" />



---

## Deploy to the kubernetes

```
sudo chmod +x kubeadm.sh
```

[follow the doc to install](https://github.com/SeshadriRC/DevOps-Docs/blob/main/Kubernetes/kubeadm_jenkins_maven_docker.sh)


- Install the plugin `kubernetes cli`
- using the config file , we can login to the cluster. from `apiversion upto last`.
- upload the text file.

<img width="1918" height="662" alt="image" src="https://github.com/user-attachments/assets/1f06e106-cfc4-44d3-903d-5327884a5af1" />


<img width="1917" height="1012" alt="image" src="https://github.com/user-attachments/assets/f28f6ab1-afe6-4885-863d-4d056200752f" />


<img width="162" height="201" alt="image" src="https://github.com/user-attachments/assets/a5bc7232-ace9-4fc5-ad30-007746cbc429" />



<img width="1918" height="855" alt="image" src="https://github.com/user-attachments/assets/8ae7bd97-ff5b-4d45-bca6-d0b0f7e5dd18" />


<img width="1918" height="558" alt="image" src="https://github.com/user-attachments/assets/8a70f958-3b71-4d53-8676-57037067eff6" />


- pipeline syntax


<img width="1917" height="663" alt="image" src="https://github.com/user-attachments/assets/aef68799-b3e2-4335-a50c-18294084c461" />


- Only `credentialID` is required, remove all other things.

<img width="1357" height="443" alt="image" src="https://github.com/user-attachments/assets/57812f74-bfbc-4b4a-ba40-8d2cc0799d3e" />

<img width="1893" height="593" alt="image" src="https://github.com/user-attachments/assets/dea494e9-edc6-4a0c-8956-5c4b1440a399" />

