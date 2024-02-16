pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    docker.build('nginx')
                }
            }
        }        
        stage('Deploy') {
            agent {
                label 'agent'
            }
            steps {
                script {
                    checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/JeevaArasu/jenkins-Master-Slave-Sample.git']])
                    sh 'chmod +x script.sh'
                    sh './script.sh'
                }    
            }
        }
    }
}
