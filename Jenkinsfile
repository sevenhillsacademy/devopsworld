pipeline {
    agent any
    stages {
        stage("source code") 
        {
            git branch: 'main', changelog: false, poll: false, url: 'https://github.com/sevenhillsacademy/devopsworld.git'
        }
    }
}
