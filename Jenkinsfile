pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello from GitHub hook trigger'
            }
        }
        stage('Build') {
            steps {
                echo 'building'
            }
        }
        stage('Deploy') {
            steps {
                echo 'deploying'
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: 'MyAWS',
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]){
                        sh(script: 'aws s3 cp /var/lib/jenkins/workspace/JenkinsPipeline/index.html s3://test-jenkins-morohashi/')
                }
            }
        }
        stage('Test') {
            steps {
                echo 'testing'
            }
        }
        stage('Release') {
            steps {
                echo 'releasing'
            }
        }            
    }
}
