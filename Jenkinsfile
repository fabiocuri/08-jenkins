#!/usr/bin/env groovy
library identifier: 'jenkins-shared-library@main', retriever: modernSCM(
        [$class: 'GitSCMSource',
        remote: 'https://github.com/fabiocuri/jenkins-shared-library.git',
        credentialsId: 'gitlab-credentials'])

pipeline {

  agent any
  
  stages {

    stage('Checkout') {
        steps {
            git credentialsId: 'github-secret-token', url: 'https://github.com/fabiocuri/08-jenkins', branch: 'master'
        }
    }

    stage("build-image") {
      steps {
        buildImage 'fabiocuri/jenkins-demo:1.0'
      }
    }
  
    stage("push-image") {
      steps {
        dockerLogin()
        dockerPush 'fabiocuri/jenkins-demo:1.0'
      }
    }
          
  }
}
