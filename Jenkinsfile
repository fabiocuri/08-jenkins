pipeline {
  
  agent any

  environment {
    SERVER_CREDENTIALS = credentials("github_credentials")
  }
  
  stages {
    
    stage("build") {
      steps {
        echo "building the app"
      }
    }
    
    stage("test") {
      steps {
        echo "testing the app"
      }
    }

    stage("deploy") {
      steps {
        echo "deploying the app"
        echo "using credentials from ${SERVER_CREDENTIALS}"
      }
    }
  }
}
