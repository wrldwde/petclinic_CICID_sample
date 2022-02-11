pipeline {
    agent {
        label 'linux'
    }
    stages {
      stage('SonarQube Analysis') {
            steps {
                    sh 'chmod +x mvnw'
                    sh 'mvn clean verify -Dcheckstyle.skip sonar:sonar'
            }
        }
        stage("Create docker image") {
            steps {
                sh 'sudo docker build -t ubuntu/petclinic:$BUILD_NUMBER -t ubuntu/petclinic:latest .'
            }
        }
   }          
}
