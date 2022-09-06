pipeline {
    agent any
    
    environment {
        imageName = "PHP-TODO"
        registryCredentials = "nexus"
        registry = "54.162.107.209:8083"
        dockerImage = ''
    }

  stages {

     stage("Initial cleanup") {
          steps {
            dir("${WORKSPACE}") {
              deleteDir()
            }
          }
        }

    stage('Checkout SCM') {
      steps {
            git branch: 'main', url: 'https://github.com/ssen280/php-todo.git'
      }
    }
    // Building Docker images
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build imageName
        }
      }
    }
  }
}
