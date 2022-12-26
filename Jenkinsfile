pipeline { 

    environment { 
        
        registry = "levdevops/nodejs" 

        registryCredential = "dockerhub"

        dockerImage = ''
     
        
    }

    agent any 

    stages { 

        stage('Cloning our Git') { 

            steps { 

                git 'https://github.com/Lyov-DevOps/nodejs-project.git' 

            }

        } 

        stage('Building our image') { 

            steps { 

                script { 
                    echo 'Building'
                    dockerImage = docker.build registry:$BUILD_NUMBER
                 
                }

            } 

        }

        stage('Deploy our image') { 

            steps { 

                script { 
                    echo 'Deploying'
                    docker.withRegistry( '', registryCredential ) { 
                        dockerImage.push('')
                      
                        
                    }

                } 

            }
        }

     stage('Cleaning up') { 

            steps { 

                sh "docker rmi $registry:$BUILD_NUMBER" 

            }

        } 

    }

}    


