pipeline { 

    environment { 
        
        registry = "levdevops/nodejs" 

        registryCredential = "dockerhub"
        dockerImage = ''
        version = "v.2.4"
        
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
                    dockerImage = docker.build registry("${env.version}")
                 
                }

            } 

        }

        stage('Deploy our image') { 

            steps { 

                script { 
                    echo 'Deploying'
                    docker.withRegistry( '', registryCredential ) { 

//                         dockerImage.push("${env.BUILD_NUMBER}")
                        dockerImage.push()
                    }

                } 

            }
        }
}
    
}
