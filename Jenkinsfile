pipeline {
    agent any
    options {
        disableConcurrentBuilds()
    }

    stages {

        stage('Start') {

                steps {
                  
                  script {
                        sh '''
                        
                        
                        echo "echo 'Olahhhh mundo !!!'"
                        

                        '''
             
                      }

                  }
                }
          stage('Pre-flight') {

            agent {
                docker { image '701339036578.dkr.ecr.sa-east-1.amazonaws.com/docker-base-terraform-ansible-packer:latest'
                       args '-i --entrypoint='
                       }
            }

            steps {
              
              script {
                withCredentials([
                usernamePassword(credentialsId: 'seraph', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')
              ])
                    sh '''
                    ./bolota.sh
                    '''
         
                  }

              }
            }
   } // stages
} // pipeline
