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
               sh 'docker build -t appjs:1.11 .'
                
                
//                 script { 
//                     echo 'Building'
//                     dockerImage = docker.build registry
                 
                }

            } 

        

        stage('Deploy our image') { 

            steps { 
                sh 'docker tag appjs:1.11 levdevops/appjs:1.11 '
                sh 'echo $dockerhub_PSW | docker login -u $dockerhub_USR --password-stdin'
                sh 'docker push levdevops/appjs:1.11 '
//                 script { 
//                     echo 'Deploying'
//                     docker .withRegistry( '', registryCredential ) { 
                    
//                     dockerImage.push("v.1.9")
                   
                    }

                } 
 


