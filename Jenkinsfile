pipeline {
     agent {
        label 'my-slave'
    }

    environment {
        IMAGE_NAME = "i27-helpdesk-ui:dev"
        CONTAINER_NAME = "i27-ui"
    }

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/i27academy/i27-helpdesk-ui.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${IMAGE_NAME} --build-arg NEXT_PUBLIC_API_BASE_URL=http://34.6.151.76:8080 ."
            }
        }

        stage('Build container') {
            steps {
                sh "docker run -d --name ${CONTAINER_NAME} -p 3000:3000 ${IMAGE_NAME}"
            }
        }
    }
}
