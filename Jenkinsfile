pipeline {
    agent any
    
  

    stages {
        stage('Checkout') {
            steps {
                // Récupérer le code source du projet depuis un référentiel git
                // (vous pouvez modifier cette étape en fonction de votre configuration)
                git 'https://github.com/vincentvgit/calculator.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                
                script {
                    def dockerImage = docker.build('calculator3')
                    dockerImage.push()
                }
            }
        }
        stage ('Docker Tag') {
            steps {
                script {
                    sh 'sudo docker tag calculator3 vincentvdocker/calculator3'
                    
                }
            }
        }
         stage('Login') {
      steps {
        script{
            sh 'sudo docker Login -u vincentvdocker -p Nufan151*'
        }}
      }
        
        stage('Push to Docker Hub') {
            steps {
                
                script {
                     
                        sh 'sudo docker push vincentvdocker/calculator3'
                    }
                }
            }
        }
    }
