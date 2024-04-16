pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'compiling the code...'
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'running unit tests...'
        sh 'mvn clean test'
      }
    }

    stage('package') {
      parallel {
        stage('package') {
          steps {
            archiveArtifacts 'target/*.war'
            echo 'generating artifacts...'
            sh 'mvn package -DskipTests'
          }
        }

        stage('Test echo') {
          steps {
            sh 'echo "Hello"'
          }
        }

        stage('Test Echo 2') {
          steps {
            sh 'echo "world"'
          }
        }

      }
    }

  }
  tools {
    maven 'Maven 3.6.3'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}