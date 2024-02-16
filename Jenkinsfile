pipeline {
    agent {
        label 'slave'
    }
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t mynginsapp .'
            }
        }      
        stage('Deploy') {
            agent {
                label 'slave'
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
