pipeline {
    agent { label 'iti-lab2'}

    stages {
        stage('build') {
            steps {
                echo "This is build stage number ${BUILD_NUMBER}"
                withCredentials([usernamePassword(credentialsId: 'iti-lab2-dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                sh """
                    docker login --username ${USERNAME} --password ${PASSWORD}
                    docker build -t ${USERNAME}/iti_lab-bakehouse:${BUILD_NUMBER} .
                """
                }
            }
        }
        stage('push') {
            steps {
                echo "This is push stage number ${BUILD_NUMBER}"
                withCredentials([usernamePassword(credentialsId: 'iti-lab2-dockerhub', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                sh """
                    docker push ${USERNAME}/iti_lab-bakehouse:${BUILD_NUMBER}
                    export LAST_PUSH_NUMBER=${BUILD_NUMBER}
                """
                }
            }
        }
        }
    }
