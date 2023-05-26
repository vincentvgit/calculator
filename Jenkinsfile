pipeline {
    docker.image('calculator/new').withRun('-p 8181:80') { c ->

        sh 'docker ps'

        sh 'curl localhost'
      stages {
        stage('log version info') {
      steps {
        sh 'mvn --version'
        sh 'mvn clean install'
      }
    }
  }
}
        
}
