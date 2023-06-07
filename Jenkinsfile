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

sshPublisher(publishers: [sshPublisherDesc(configName: 'vincent-docker', sshCredentials: [encryptedPassphrase: '{AQAAABAAAAAQxRxUgFgSm7zsYshq8ajpgrQN1FHdmgsQBJxPsM4cg64=}', key: '', keyPath: '', username: 'vincent'], transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'docker run -d -p 8182:3000 vincentvdocker/calculator01', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: true)]) 8183:3000 vincentvdocker/calculator01', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
