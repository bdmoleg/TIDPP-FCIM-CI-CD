#!groovy

pipeline {


    agent any


    stages() {

        stage("Procesul de Build") {
        
            steps {
                echo "Build number ${BUILD_NUMBER} and ${BUILD_TAG}"
            }

        }

        stage("Procesul de Testing") {
        
            steps {
                echo "Testing stage"
            }

        }

        stage("Delivery/Deployment") {
        
            steps {
                echo "Deployment stage"
            }

        }

    }




}
