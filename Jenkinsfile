#!/usr/bin/env groovy
library identifier: 'jenkins-shared-library@main', retriever: modernSCM(
        [$class: 'GitSCMSource',
        remote: 'https://github.com/fabiocuri/jenkins-shared-library.git',
        credentialsId: 'gitlab-credentials'])

pipeline {

  agent any
  
  stages {

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
          
    stage("deploy") {
      steps {
        buildJar()
      }
    }
  }
}
