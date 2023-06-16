pipeline{
        agent label {'agent1'}
	
		stages{
			stage ("Pull the code from SCM"){
				steps {
					git branch: 'main', url: 'https://github.com/ps103/node_js-pro.git'
					}
				}
			stage (" Build the code "){
				steps {
					sh 'docker build . -t psharma10394/nodejs-app:latest'
					
					}
				}
				stage ( " push the image "){
				steps {
				withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword',usernameVariable: 'dockerHubUser')]){
					sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
					sh 'docker push psharma10394/nodejs-app:latest'
						}
					}
				}
				stage("Test"){
				steps{
				    echo "To test the code "
				    
				  }
				}	
				stage("deploy"){
				steps{
				    echo "code is ready to deploy"
				     sh 'docker-compose down && docker-compose up -d'
				    
				  
				    
				}
				}	
		
}
}

