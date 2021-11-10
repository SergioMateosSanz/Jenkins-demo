pipeline { 
    agent any  
    stages { 
        stage('Init') { 
            steps { 
               echo 'This is the pipeline begin.' 
            }
        }
      stage('Test') { 
            steps { 
               sh 'mvn test' 
            }
        }
      post {
        always {
            archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
            junit 'build/reports/**/*.xml'
        }
      }
      stage('Build') { 
            steps { 
               sh 'mvn package -Dmaven.test.skip=true' 
            }
        }
    }
}
