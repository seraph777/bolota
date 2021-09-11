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
                        touch bolota.sh
                        echo "hostname" >> bolota.sh
                        echo "echo 'Olá mundo !!!'"
                        chmod +x bolota.sh
                        packer --version

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
                    sh '''
                    ./bolota.sh
                    # terraform --version
                    # ansible --version
                    # packer --version

                    '''
         
                  }

              }
            }
   } // stages
} // pipeline
