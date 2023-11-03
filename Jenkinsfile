pipeline {
    agent any

    stages {
        stage('Sonar Analysis'){
            steps {
                echo 'Testing..'
                sh 'cd webapp && sudo docker container run --rm -e SONAR_HOST_URL="http://65.0.5.238:9000" -e SONAR_LOGIN="sqp_d658046d8620cd16d7a982285fade613524268c5" -v ".:/usr/src" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms'
            }
        }
    stage('Build lms frontend') {
            steps {
                echo 'Frontend building..'
                sh 'cd webapp && sudo npm install && npm run build'
            }
        }
        stage('Release') {
            steps {
                echo 'Releasing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
