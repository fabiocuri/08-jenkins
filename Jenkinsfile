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
          usernamePassword(credentials: "github_credentials", usernameVariable: GITHUB_USER, passwordVariable: GITHUB_PASSWORD)
        ]){
          echo $GITHUB_USER
          echo $GITHUB_PASSWORD
        }
      }
    }
  }
}
