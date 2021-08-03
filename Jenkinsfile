pipeline {
  agent {
    node {
      label 'nodejs-centos7'
    }

  }
  stages {
    stage('CheckOut Code') {
      steps {
        git(url: 'https://github.com/davidvr1/NodeJS-EmptySiteTemplate.git', branch: 'master', changelog: true, poll: true, credentialsId: 'github')
      }
    }

  }
}