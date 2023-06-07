pipeline {
    agent any

 
    stages {
        
        stage("Maven clean build") {
             steps { 
                  def mavenHome = tool name:"Maven-3.8.6", type: "maven"
                  def mavenCMD = "${mavenHome}/bin/mvn"
                  sh "${mavenCMD} clean package"
   }
}
        stage ('Docker Build') {
            steps {
                script {
                    sh 'docker build -t calculator01 .'
                    echo 'Build Image Completed'
                }
            }
        }

        stage ('Docker Tag') {
            steps {
                script {
                    sh 'docker tag calculator01 vincentvdocker/calculator01'
                    echo 'Tag Image Completed'
                }
            }
        }

        stage('Docker Login') {
            steps {
                script {
                    sh 'docker login -u vincentvdocker -p Nufan151*+' 
                    echo 'Login Completed'
                }
            }
        }

        stage ('Docker Push') {
            steps {
                script {
                    sh 'docker push vincentvdocker/calculator01'
                    echo 'Push Completed'
                }
            }
        }
    }
}
