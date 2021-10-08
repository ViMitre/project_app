pipeline{

    agent any

    environment {
        DOCKERHUB_CREDENTIALS=credentials('SRE_final_project_DockerHub_credentials')
    }

    stages {

        stage('Build') {

            steps {
                sh 'docker build -t vimitre/sre_app .'
            }
        }

        stage('Login') {

            steps {
                sh 'docker login -u $DOCKERHUB_CREDENTIALS_USR -p $DOCKERHUB_CREDENTIALS_PSW'
            }
        }

        stage('Push') {

            steps {
                sh 'docker push vimitre/sre_app'
            }
        }
    }

    post {
        always {
            sh 'docker logout'
        }
    }
}
