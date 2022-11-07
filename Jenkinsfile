pipeline{
agent any


    environment {

        TAG = "${DATE}.${BUILD_NUMBER}"
    }
   stages{



			    stage('Build docker image'){
                             steps{
                                     docker.build("203jmt0064/angular:${TAG}")
                                      docker.build("203jmt0064/angular:latest")
                                


                             }
                         }


		 stage('push image to docker hub'){
        steps{
            script{
            withCredentials([string(credentialsId: 'DOCKER_CRED', variable: 'DOCKERHUBP')]) {

                sh 'docker login -u 203jmt0064 -p ${DOCKERHUBP}'

                sh 'docker image push 203jmt0064/angular:${TAG}'

                sh 'docker image push 203jmt0064/angular:latest'

            }

            }


          }}

  }}
