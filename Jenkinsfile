pipeline {
    agent any

    stages {
        stage('test') {
            steps {
                sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL='http://3.238.132.8:9000' 
                    -e SONAR_LOGIN='sqp_7f372beac8bc24607c93915be69dce6e94153b4c' -v '.:/usr/src'
                    sonarsource/sonar-scanner-cli -Dsonar.projectKey=LMS'
                'sonar testing..'
            }
        }
    }
}
