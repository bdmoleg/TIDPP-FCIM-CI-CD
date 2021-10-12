#!groovy

pipeline {


    agent any

     options {
          buildDiscarder(logRotator(numToKeepStr: '2'))
          timestamps()
     }

     parameters {
         string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Helpful description for Person param')

         text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some important info about the person biography')

         booleanParam(name: 'CHECKBOX', defaultValue: true, description: 'Check me if you can')

         choice(name: 'CHOICE', choices: ['First', 'Second', 'Third'], description: 'Pick something')

         password(name: 'PASSWORD', defaultValue: 'VERYSECRET', description: 'Enter a password you already know')
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

      post {
          always {

               echo "${BUILD_TAG}"
               echo "${params.PERSON}"
               echo "${params.BIOGRAPHY}"
               echo "${params.CHECKBOX}"
               echo "${params.CHOICE}"
               echo "${params.PASSWORD}"


          }


}
