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

    stage('Install dependecies [Build]') {
      steps {
        sh 'npm install'
      }
    }

    stage('running the application') {
      steps {
        sh 'npm start &'
      }
    }

    stage('test the app') {
      steps {
        sh 'curl localhost:8080'
      }
    }

    stage('kill app') {
      steps {
        sh 'pkill -f node'
      }
    }

    stage('Package') {
      steps {
        zip(zipFile: 'package.zip', archive: true, dir: '.', overwrite: true)
        archiveArtifacts(artifacts: 'package.zip', onlyIfSuccessful: true)
        cleanWs(cleanWhenSuccess: true)
      }
    }

    stage('notify slack') {
      steps {
        slackSend(failOnError: true, channel: 'devops_kamatech')
      }
    }

  }
}