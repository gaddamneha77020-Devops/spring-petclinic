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
        stage ("build and scan") {
          steps {
            withCredentials([string(credentialsID:'SONAR',variable:"SONAR_TOKEN")]) {
            withSonarQubeEnv("sonar_id") {  
            sh """mvn package sonar:sonar \
                  -Dsonar.projectKey=gaddamneha77020-Devops_spring-petclinic \
                  -Dsonar.organization=gaddamneha77020-devops \
                  -Dsonar.host.url=https://sonarcloud.io/ \
                  -Dsonar.login=$SONAR_TOKEN """
              }
            }
          } 
        }
        
    }
}