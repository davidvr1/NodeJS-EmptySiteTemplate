pipeline {
  agent {
    node {
      label 'nodejs-centos7'
    }

  }
  stages {
    stage('') {
      steps {
        git(url: 'https://github.com/davidvr1/NodeJS-EmptySiteTemplate.git', branch: 'master', changelog: true, poll: true, credentialsId: 'github')
      }
    }

  }
}