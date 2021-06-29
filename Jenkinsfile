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
        sh '''
            rm -fR *
            aws s3 cp s3://suchsatbucket/Staticwebsite.zip .
            unzip Staticwebsite.zip
            scp index.html root@10.0.15.106:/var/www/html/
          '''
      }
    }

  }
}