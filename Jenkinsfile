pipeline {
    agent any
    environment {
        registry = "stoneherc/openai-app"
        registryCred = "dockerhub"
    }
    stages {
        stage ('Clone this repo'){
            steps{
                git branch: 'main', url: 'https://github.com/adityamurali155/openai-image-gen.git'
            }
        }
        stage ('Build docker image') {
            steps{
                script{
                    app = docker.build registry + ":V$BUILD_NUMBER"
                }
            }
        }
        stage('Upload Image'){
          steps{
            script {
              docker.withRegistry('', registryCred) {
                app.push("V$BUILD_NUMBER")
              }
            }
          }
        }
        stage('Remove Unused docker image') {
          steps{
            sh "docker rmi $registry:V$BUILD_NUMBER"
          }
        }
    }
}