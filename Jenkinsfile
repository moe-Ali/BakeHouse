
pipeline {
    agent { label 'iti-lab2'}

    stages {
        stage('Deploy') {
            steps {
                echo "This is deploy stage number ${BUILD_NUMBER}"
                withCredentials([file(credentialsId: 'iti-lab2-kubeconfig',variable: 'KUBECONFIGFILE')]) {
                sh """
                    export BUILD_NUMBER= \$LAST_PUSH_NUMBER
                    mv Deployment/deploy.yaml Deployment/deploy.yaml.tmp
                    cat Deployment/deploy.yaml.tmp | envsubst > Deployment/deploy.yaml
                    rm -f Deployment/deploy.yaml.tmp
                    kubectl apply -f Deplyoment --kubeconfig ${KUBECONFIGFILE}
                """
                }
            }
        }
        }
    }
