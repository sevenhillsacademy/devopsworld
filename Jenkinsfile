pipeline {
    agent any
    stages {
        stage("source code") {
            steps {
                echo 'Getting the source from GitHub'
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/sevenhillsacademy/devopsworld.git'
            }
        }
        stage("Build") {
            steps {
                echo 'Building the war file'
                sh 'mvn clean install'
            }
        }
        stage("Deploy") {
            steps {
                echo 'Deploy the war into WebServer'
                deploy adapters: [tomcat9(credentialsId: 'tomcatadmin', path: '', url: 'http://3.87.14.43:8000/')], contextPath: 'devopsworld2022', war: '**/*.war'
            }
        }
    }
}
