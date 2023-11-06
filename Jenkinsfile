pipeline {
    agent any

    stages {
        stage('Sonar Analysis'){
            steps {
                echo 'Testing..'
                sh 'cd webapp && sudo docker container run --rm -e SONAR_HOST_URL="http://35.154.54.7:9000" -e SONAR_LOGIN="sqp_ddedeaffe74b8ae9e8114445af51edeedfca761c" -v ".:/usr/src" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms'
            }
        }
    stage('Build lms frontend') {
            steps {
                echo 'Frontend building..'
                sh 'cd webapp && sudo npm install && npm run build'
            }
        }
        stage('Build lms backend') {
            steps {
                echo 'Backend building..'
                sh 'cd api && sudo npm install && npm run build'
            }
        }
        stage('Release lms frontend') {
            steps {
                script{
              def packageJSON = readJSON file: 'webapp/package.json'
              def packageJSONVersion = packageJSON.version
                    sh 'sudo npm install && npm run build'
              echo "${packageJSONVersion}"
              sh "zip webapp/dist-${packageJSONVersion}.zip -r webapp/dist"
              sh "curl -v -u admin:admin --upload-file webapp/dist-${packageJSONVersion}.zip http://13.235.71.214:8081/repository/lms/"      
            }
        }
    }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
