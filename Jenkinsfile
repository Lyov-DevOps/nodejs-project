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
                    dockerImage = docker.build registry  
                 
                }

            } 

        }

        stage('Deploy our image') { 

            steps { 

                script { 
                    echo 'Deploying'
                    docker.withRegistry( '', registryCredential ) { 
                        dockerImage.push("v.2.2")
                        dockerImage.push( "${env.BUILD_NUMBER}" )
                        
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
}

