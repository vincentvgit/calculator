pipeline {
    agent any
    
  

    stages {
        stage('Checkout') {
            steps {
             
                git 'https://github.com/vincentvgit/calculator.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                
                script {
                    def dockerImage = docker.build('calculator01')
                    
                }
            }
        }
        stage ('Docker Tag') {
            steps {
                script {
                    sh 'docker tag calculator01 vincentvdocker/calculator01'
                    
                }
            }
        }
         stage('Login') {
      steps {
        script{
            sh 'docker login -u vincentvdocker -p dckr_pat_WLTjxmlF105W-k2SLxSQhvVAUCI'
        }}
      }
        
        stage('Push to Docker Hub') {
            steps {
                
                script {
                     
                        sh 'docker push vincentvdocker/calculator01'
                    }
                }
            }
        }
    }
          node {
            def remote = [:]
            remote.name = 'vincent-docker'
            remote.host = '51.103.94.88'
            remote.user = 'vincent'
            remote.password = 'Azertyuiop123'
            remote.allowAnyHosts = true
            stage('Remote SSH') {
                sshCommand remote: remote, command: "docker run -d -p 8182:3000"
            }
          }
