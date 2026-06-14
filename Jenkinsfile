pipeline {
    agent any
    
    tools{
        jdk 'jdk'
        maven 'maven3'
    }
    environment{
        SCANNER_HOME= tool 'sonar-scanner'
    }

    stages {
        stage('Git Checkout') {
            steps {
                git 'https://github.com/SeshadriRC/Jenkins-Zero-To-Hero.git'
            }
        }
        
        stage('Code Compile') {
            steps {
                sh 'cd java-maven-sonar-argocd-helm-k8s/spring-boot-app && mvn clean package'
            }
        }
        
        stage('SonarQube Analysis'){
            steps{
                withSonarQubeEnv('SonarQube'){
                    sh """$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=new \
                    -Dsonar.java.binaries=. \
                    -Dsonar.projectKey=new"""
                }
            }
        }
        
     stage('Docker Build and Push') {
    environment {
        DOCKER_IMAGE = "sesharc/end-to-end:${BUILD_NUMBER}"
        REGISTRY_CREDENTIALS = credentials('f239455a-2d14-4e86-aeaa-db90afa73056')
    }

    steps {
        script {

            // Build image
            sh "docker build -t ${DOCKER_IMAGE} ."

            // Login + push
            docker.withRegistry('https://index.docker.io/v1/', 'f239455a-2d14-4e86-aeaa-db90afa73056') {
                docker.image("${DOCKER_IMAGE}").push()
            }
        }
    }
}
   stage('Deploy to K8s'){
       steps{
           script{
               withKubeCredentials(kubectlCredentials: [[credentialsId: '03e14534-41a1-43ee-abba-e356b620034c']]) {
                   sh 'kubectl apply -f k8s/deployment.yaml'
           }
           }
       }
   }
    }
}
