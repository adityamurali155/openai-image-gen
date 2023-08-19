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
    }
}