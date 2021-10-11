pipeline{

    agent any

    environment {
        DOCKERHUB_CREDENTIALS=credentials('SRE_final_project_DockerHub_credentials')
        REPO_NAME="vimitre/sre_app"
    }

    stages {

        stage('Build') {

            steps {
                // script {
                //     docker.build REPO_NAME + ":$BUILD_NUMBER"
                // }
                sh "docker build -t vimitre/sre_app:$BUILD_NUMBER ."
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
