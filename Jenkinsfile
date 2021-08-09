pipeline {
    agent any

    environment {
        SETTINGS_XML = credentials('maven-settings-config')
    }

    stages {
        stage('Example') {
            steps {
                echo 'Hello, Maven'
                bat 'mvn --version'
                //sh 'mvn --version'
            }
        }
        stage('clone') {
            steps {
                // Get some code from a GitHub repository
                git branch: 'dev', url: 'https://github.com/Srishty1501/Jenkins_Demo.git'
            }

            
        }
        stage ('Build') {
            steps {
                bat 'mvn -s $SETTINGS_XML clean install' 
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
        }

        stage ('deploy artifacts') {
            steps {
               bat 'mvn -s $SETTINGS_XML deploy -Dbuildnumber=${env.BUILD_NUMBER} -DbuildUrl=${env.BUILD_URL} -DagentName=${env.NODE_NAME}' 
            }
        }
    }
}
