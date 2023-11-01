pipeline{
   agent any
  stages{
    stage('sonar Analysis'){
      steps{
        echo 'Testing'
        sh 'cd webapp && sudo docker run --rm -e SONAR_HOST_URL="http://54.89.198.242:9000" -e 
        SONAR_LOGIN="sqp_627cf1b5ba0e44d182981783016a13096ee6c07c" -v ".:/usr/src" sonarsource/sonar-scanner-cli -Dsonar.projectKey=lms'
      }
    }
    
    stage('build lms frontend'){
      steps{
        echo 'frontend building'
        sh 'cd webapp && npm install && npm run build'
      }
    }
    
    stage('build lms backend'){
          steps{
            echo 'backend building'
            sh 'cd api && npm install && npm run build'
          }
    }

    stage('Release LMS frontend'){
          steps{
            script{
              def packageJSON = readJSON file: 'webapp/package.json'
              def packageJSONVersion = packageJSON.version
              echo "${packageJSONVersion}"
              sh "zip webapp/dist-${packageJSONVersion}.zip -r webapp/dist"
              sh "curl -v -u admin:admin --upload-file webapp/dist-${packageJSONVersion}.zip http://54.89.198.242:8081/repository/lms/"
            }
          }
    }

    stage('Release LMS backend'){
      steps{
        script{
        def packageJSON = readJSON file: 'webapp/package.json'
        def packageJSONVersion = packageJSON.version
        echo "${packageJSONVersion}"
        sh "zip api/dist-${packageJSONVersion}.zip -r api/dist"
        sh "curl -v -u admin:admin --upload-file api/dist-${packageJSONVersion}.zip http://54.89.198.242:8081/repository/lms/"
        }
      }
    }
  }
}
