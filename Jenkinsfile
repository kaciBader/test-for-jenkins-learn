pipeline {
  agent {
    docker {
      image 'php:8.3.4-alpine3.19'
    }
  }
  stages {
    stage('build') {
      steps {
        sh 'php --version'
      }
    }
  }
  post {
        always {
            echo 'One way or another, I have finished'
           // deleteDir() /* clean up our workspace */
        }
        success {
            echo 'I succeeded!'
            mail  to: 'bader.kaci@gmail.com',
                  subject: "Success Pipeline: ${currentBuild.fullDisplayName}",
                  body: "Something is success with ${env.BUILD_URL}"
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
    } 
}
