pipeline {
  agent {
        docker {
          image 'python:3.7.2'
          args '--user 0:0'
        }
      }
  stages {
    stage('build') {
      steps {
        sh """
            pip install -r requirements.txt --user
        """

      }
    }
    stage('test') {
      steps {
       // sh 'pip install -r requirements.txt --user'
        sh 'python test.py'
      }
      post {
        always {
          junit 'test-reports/*.xml'
        }
      }    
    }
  }
}
