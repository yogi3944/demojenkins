pipeline {
    agent any
    environment{
        name = "Yogesh"
    }
    parameters {
        string(name: 'person', defaultValue: 'Preeti', description: 'who are you')
        booleanParam(name: 'isMale', defaultValue: true, description: "")
        choice(name: 'City', choices: ['Jaipur','Mumbai','Jamshedpur'], description: "")
        
    }

    stages {
        stage('Test') {
            steps {
                sh 'date'
                sh 'pwd'
                echo 'Hello test'
            }
        }
        stage('Build') {
            steps {
                sh '''
                ls
                date
                pwd
                cal 2022
                echo 'Hello build'
                '''
            }
        }
        stage('Deploy on Test and environment variables') {
            environment {
                username = "Pooja"
            }
            steps {
                sh 'echo "$BUILD_ID"'
                sh 'echo "$name"'
                sh 'echo "$username"'
                sh 'echo "$person"'
                sh 'echo "$isMale"'
                echo 'Hello deploy on test'
            }
        }
        stage('Continue') {
            input {
                message "Should we continue"
                ok "Yes we continue"
            }
            steps {
                sh 'echo "$username"'
                echo 'Hello deploy on prod'
            }
        }
        stage('Deploy on Prod') {
            steps {
                sh 'echo "$username"'
                echo 'Hello deploy on prod'
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
        failure { 
            echo 'Failure'
        }
        success { 
            echo 'Success'
        }
    }
}
