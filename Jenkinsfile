pipeline {
    agent any

    stages {
        stage('Sonar Analysis') {
            steps {
                echo 'Testing..'
                sh 'cd webapp && sudo docker run --rm -e SONAR_HOST-URL"http://http://3.111.34.99:9000" -e SONAR_LOGIN="sqp_c47aa3f6d2485890ee163071344e9aca2114c492" -v ".:/usr/src/" sonarsource/sonar-scanner-cli -Dsonar.projectkey=lma'
            }
        }
    stage('Build') {
            steps {
                echo 'Building..'
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
