pipeline {
    agent {label "spc"}
    triggers {
        pollSCM ("* * * * *")
    }
    stages {
        stage ("git checkout") {
          steps {
            git url: "https://github.com/spring-projects/spring-petclinic.git",
              branch: "main"
          }
        }
        stage ("build") {
          steps {
            sh "mvn package"
          }
        }
    }
}