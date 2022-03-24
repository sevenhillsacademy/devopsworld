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
    }
}
