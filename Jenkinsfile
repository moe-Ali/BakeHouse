pipeline {
    agent any

    stages {
        stage('develop') {
            steps {
                echo "This is Develop stage"
                echo "${build_number}"
                sh """
                    mkdir Mohamed_Ali
                """
            }
        }
        stage('test') {
            steps {
                echo 'This is Test stage'
                sh """
                    ls -la
                    
                """
            }
        }
        stage('destroy') {
            steps {
                echo 'This is Destroy stage'
                sh """
                    rm -r Mohamed_Ali
                """
            }
        }
        stage('check'){
            steps{
                echo 'This is Check stage'
                sh """
                ls
                """
            }
        }
        }
    }
