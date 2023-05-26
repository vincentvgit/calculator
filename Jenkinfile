node{
  def app

    stage('Clone') {
        checkout scm
    }

    stage('Build image') {
        app = docker.build("calculator/new")
    }

    stage('Run image') {
        docker.image('calculator/new').withRun('-p 8181:80') { c ->

        sh 'docker ps'

        sh 'curl localhost'
