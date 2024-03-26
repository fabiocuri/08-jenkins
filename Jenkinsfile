#!/usr/bin/env groovy
library identifier: 'jenkins-shared-library@main', retriever: modernSCM(
        [$class: 'GitSCMSource',
        remote: 'https://github.com/fabiocuri/jenkins-shared-library.git',
        credentialsId: 'gitlab-credentials'])

pipeline {
  
  agent any

  parameters {
    booleanParam(name: "RUN_PIPELINE", defaultValue: true, description: "")
    choice(name: "VERSION", choices: ["1.1.0", "1.2.0", "1.3.0"], description: "")
  }
  
  stages {

    stage("build-image") {
      steps {
        buildImage 'fabiocuri/jenkins-demo:1.0'
        dockerLogin()
      }
    }
  
    stage("test") {
      when {
        expression {
          params.RUN_PIPELINE
        }
      }
      steps {
        echo "Building the app ${params.VERSION} ..."
        echo "Deploying to ${ENV} environment ..."
      }
    }
          
    stage("deploy") {
      when {
        expression {
          params.RUN_PIPELINE
        }
      }
      steps {
        buildJar()
      }
    }
  }
}
