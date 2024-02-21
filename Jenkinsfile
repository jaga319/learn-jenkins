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
        timeout(time: 1,unit:'HOURS')
        disableConcurrentBuilds()
    }
    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')

        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')

        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')

        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')

        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }
    // Build //
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
                  echo 'Good morning'
                """
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
            }
        }
        stage(' checking params '){
            steps{

                sh """
                    echo 'password: ${params.PASSWORD}'
                    echo 'TOGGLE :${params.TOGGLE}'
                """
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
