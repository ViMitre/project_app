pipeline{

    agent any

    environment {
        DOCKERHUB_CREDENTIALS=credentials('SRE_final_project_DockerHub_credentials')
    }

    stages {

        stage('Build') {

            steps {
                sh 'sudo docker build -t vimitre/sre_app:latest /tmp/project_app/'
            }
        }

        stage('Login') {

            steps {
                sh 'sudo docker login -u $DOCKERHUB_CREDENTIALS_USR -p $DOCKERHUB_CREDENTIALS_PSW'
            }
        }

        stage('Push') {

            steps {
                sh 'sudo docker push vimitre/sre_app:latest'
            }
        }
    }

    post {
        always {
            sh 'sudo docker logout'
        }
    }
}
