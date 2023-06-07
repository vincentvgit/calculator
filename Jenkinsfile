pipeline {
    agent any

    stages {
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
