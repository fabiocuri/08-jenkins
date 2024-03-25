pipeline {
  
  agent any
  
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

        withCredentials([
          usernamePassword(credentials: "github_credentials", usernameVariable: USER, passwordVariable: PWD)
        ]){
          echo $GITHUB_USER
          echo $GITHUB_PASSWORD
        }
      }
    }
  }
}
