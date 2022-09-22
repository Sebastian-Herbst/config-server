pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(branch: 'main', url: 'https://github.com/Sebastian-Herbst/config-server.git')
      }
    }

    stage('List directory') {
      parallel {
        stage('List directory') {
          steps {
            sh 'ls -la'
          }
        }

        stage('Package') {
          steps {
            withGradle()
          }
        }

      }
    }

  }
}