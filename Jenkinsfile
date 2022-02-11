pipeline {
    agent {
        label 'linux'
    }
    stages {
      stage('SonarQube Analysis') {
            tools {
                maven 'maven_sonarqube'
            }
            environment {
                scannerHome = tool 'sonarqube'
            }
            steps {
                withSonarQubeEnv('sonar_for_petclinic') {
                    sh 'chmod +x mvnw'
                    sh 'mvn clean verify -Dcheckstyle.skip sonar:sonar'
                }
            }
        }
        stage("Create docker image") {
            steps {
                sh 'sudo docker build -t ubuntu/petclinic:$BUILD_NUMBER -t ubuntu/petclinic:latest .'
            }
        }
   }          
}