pipeline {
    agent {
        node {
            label 'docker'
        }
    }
    
    stages {
        stage ('Clone the repository') {
            steps {
                git branch: 'main', url: 'https://github.com/adityamurali155/openai-image-gen.git'
            }
        }
        stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'sonar-scanner';
            }
            steps{
                withSonarQubeEnv('sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
  }
    }
    
}