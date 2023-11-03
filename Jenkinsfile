pipeline {
    agent any

    stages {
        stage('Sonar Analysis'){
            steps {
                echo 'Testing..'
                sh 'cd webapp && sudo docker container run --rm -e SONAR_HOST_URL="http://13.235.71.214:9000" -e SONAR_LOGIN="sqp_99a9e1085fd24263e59234a0873ae114886f1dc0" -v ".:/usr/src" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms'
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
