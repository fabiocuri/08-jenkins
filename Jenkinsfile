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
          usernamePassword(credentialsId: "github_credentials", usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')
        ]){
          echo $USERNAME
          echo $PASSWORD
        }
      }
    }
  }
}
