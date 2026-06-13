<img width="905" height="292" alt="image" src="https://github.com/user-attachments/assets/f0d8c49e-7d1e-4c39-bfc4-451852f4ab41" />

Code compile -> using maven

Static code analysis - using sonarqube

Code build -> using maven

Docker build -> using docker

Push image to dockerhub 

Deploy to K8s

used **t2 large** instance for this activity

**Plugins Installed** - Pipeline: Stage View, 

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


## Install the Maven

[follow this doc](https://github.com/gashok13193/DevOps-Docs/blob/main/MAVEN/maven.md#installing-maven-on-linuxubuntu)

