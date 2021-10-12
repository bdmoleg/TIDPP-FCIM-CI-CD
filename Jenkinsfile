#!groovy

pipeline {


    agent any

     options {
          buildDiscarder(logRotator(numToKeepStr: '2'))
          timestamps()
     }

    stages() {


        stage("Procesul de Build") {
        
            steps {
                echo "Build number ${BUILD_NUMBER} and ${BUILD_TAG}"

                sh 'python3.8 -m venv "${BUILD_TAG}" && \
                    . ${BUILD_TAG}/bin/activate && \
                    ${BUILD_TAG}/bin/pip install --upgrade pip && \
                    ${BUILD_TAG}/bin/pip install -r requirements.txt && \
                    python manage.py makemigrations && python manage.py migrate && deactivate'

            }

        }


        stage("Procesul de Testing") {
        
            steps {
                sh '. ${BUILD_TAG}/bin/activate && python manage.py test && deactivate'
            }

        }

        stage("Delivery/Deployment") {
        
            steps {
                echo "Deployment stage"
            }

        }

    }




}
