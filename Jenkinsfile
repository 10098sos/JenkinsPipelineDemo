pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('build') {
            steps {
                echo 'building'
            }
        }
                stage('Deploy') {
            steps {
                echo 'Deploying'
                withCredentials([[
                $class: 'AmazonWebServicesCredentialsBinding',
                credentialsId: 'MYAWS',
                accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]){
                    sh(script: 'aws s3 cp /var/lib/jenkins/workspace/JenkinsPipeline/index.html s3://test-env-bucketjn/')
                }
            }
        }
                stage('Test') {
            steps {
                echo 'testing'
            }
        }
                stage('release') {
            steps {
                echo 'releasing'
            }
        }
    }
}
