pipeline {
  agent {
    node {
        label 'AGENT-1'
    }
  } 
  environment{

    GREETINGS="HELLO"
  } 
  options{
        timeout(time:1,unit:'SECONDS')
    }// Build //
    stages {
        stage('Build') {
            steps {
                echo 'building...'
            }
        }
        stage('Test') {
            steps {
                sh """
                  echo 'Testing...'
                  echo '$GREETINGS'
                  sleep 10
                """
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
            }
        }
    }
    // post build 
     post { 
        always { 

            echo 'I will always run'
        }
        failure{
            echo 'job is failed , creating an alarm'
        }
        success{
            echo 'job completed successfully'
        }
    }
}
