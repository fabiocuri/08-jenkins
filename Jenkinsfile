pipeline {
  
  agent any

  parameters {
    choice(name: "VERSION", choices: ["1.1.0", "1.2.0", "1.3.0"], description: "")
    booleanParam(name: "EXECUTETESTS", defaultValue: true, description: "")
  }
  stages {
    stage("build") {
      steps {
        echo "building the app"
      }
    }
    stage("test") {
      when {
        expression {
          params.EXECUTETESTS
        }
      }
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
          echo "hi"
        }
      }
    }
  }
}
