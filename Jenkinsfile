pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        git(url: 'git@github.com:suchsatdevops/Staticwebsite.git', branch: 'develop')
      }
    }

    stage('build') {
      steps {
        sh 'zip -r Staticwebsite.zip *'
      }
    }

    stage('upload') {
      steps {
        sh 'ls'
      }
    }

    stage('deploy') {
      steps {
        sh 'ls'
      }
    }

  }
}