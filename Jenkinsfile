pipeline{
agent any


    environment {

        TAG = "${DATE}.${BUILD_NUMBER}"
    }
   stages{
    stage('Checkout GIT'){
                steps{
                    echo 'Pulling...';
                    git branch: 'main',
                    url : 'https://github.com/nourhenekheriji/DevOpsFront.git';
                             }
                             }



			    stage('Build docker image'){
                             steps{

                                    sh 'docker build -t nourhenekheriji/angular .'
                             }
                         }


		 stage('push image to docker hub'){
        steps{
            script{
            withCredentials([string(credentialsId: 'DOCKER_CRED', variable: 'DOCKERHUBP')]) {

                sh 'docker login -u 203jmt0064 -p ${DOCKERHUBP}'

                sh 'docker image push 203jmt0064/devops_exam:${TAG}'

                sh 'docker image push 203jmt0064/devops_exam:latest'

            }

            }


          }}

  }}
