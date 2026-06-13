<img width="905" height="292" alt="image" src="https://github.com/user-attachments/assets/f0d8c49e-7d1e-4c39-bfc4-451852f4ab41" />

Code compile -> using maven

Static code analysis - using sonarqube

Code build -> using maven

Docker build -> using docker

Push image to dockerhub 

Deploy to K8s

used **t2 large** instance for this activity

**Plugins Installed** - Pipeline: Stage View, Eclipse Temurin installer, Maven Integration

---

## Install jenkins and plugins


[follow this doc](https://github.com/gashok13193/DevOps-Docs/blob/main/Jenkins/Jenkins%20Setup.md)

- Allow the port for jenkins `8080`

- Test the git checkout functionality by creating a pipeline

   pipeline name: `CICD` --> Pipeline Script

- Generate the pipeline script by going to `pipeline syntax`

<img width="1276" height="643" alt="image" src="https://github.com/user-attachments/assets/a04a4db8-c4b7-414e-bb8f-26c773be463e" />

<img width="1537" height="642" alt="image" src="https://github.com/user-attachments/assets/f38ad1ca-2f95-402e-b79b-1e54b8c2d37a" />

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
## Code compile using maven

<img width="1487" height="665" alt="image" src="https://github.com/user-attachments/assets/66caa979-8b00-4660-8d63-dcefd01c001b" />

- Now build and test it

<img width="1566" height="576" alt="image" src="https://github.com/user-attachments/assets/500a4605-3d37-4acf-b09a-fa7fcf1f6be0" />

---

## Install the SonarQube

[follow-this-doc-go-to-package-step](https://github.com/gashok13193/DevOps-Docs/blob/main/SonarQube/SonarQube.md)

```bash
sudo apt install unzip
```

---
