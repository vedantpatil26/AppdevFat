pipeline {
    agent any
    environment {
        PATH = "C:/Maven/apache-maven-3.9.5/bin$PATH"
	JAVA_HOME = "C:/Java/jdk-17.0.5"
        // Add other environment variables as needed
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                bat "C:\\Windows\\System32\\cmd.exe /c mvn clean install"
            }
        }
        stage('Build Image'){
            steps {
                bat "C:\\Windows\\System32\\cmd.exe /c docker build -t my-maven-docker-project.jar ."
            }
        }
        stage("Docker Login"){
            steps {
                bat "C:\\Windows\\System32\\cmd.exe /c docker login --username m0inak --password Docker@moinak"
            }
        }
        stage("Docker add tag"){
            steps {
                bat "C:\\Windows\\System32\\cmd.exe /c docker tag my-maven-docker-project.jar m0inak/my-maven-docker-project.jar:tag"
            }
        }
        stage("Push Image"){
            steps {
                bat "C:\\Windows\\System32\\cmd.exe /c docker push m0inak/my-maven-docker-project.jar:tag"
            }
        }
    }
}
