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
        sh 'aws s3 cp Staticwebsite.zip s3://suchsatbucket/'
      }
    }

    stage('deploy') {
      steps {
        sh 'aws s3 cp s3://suchsatbucket/Staticwebsite.zip staticwebsite'
        sh 'unzip staticwebsite'
      }
    }

  }
}