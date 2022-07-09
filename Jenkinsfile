pipeline {
    agent { node { label 'uat' } }
    stages {
        stage("source code") {
            steps {
                echo 'Getting the source from GitHub'
                git branch: 'dev_api', changelog: false, poll: false, url: 'https://github.com/sevenhillsacademy/devopsworld.git'
            }
        }
        stage("Build") {
            steps {
                echo 'Building the war file'
                sh 'mvn clean install'
            }
        }
        stage("Code Quality Analysis") {
            steps {
                echo 'Code Quality Analysis by SonarQube'
                sh 'mvn clean package sonar:sonar'
            }
        }
        stage("Deploy") {
            steps {
                echo 'Deploy the war into WebServer'
                deploy adapters: [tomcat9(credentialsId: 'tomcatadmin', path: '', url: 'http://54.209.185.165/:8000/')], contextPath: 'devopsworld2022', war: '**/*.war'
            }
        }
    }
}
