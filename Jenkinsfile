<<<<<<< HEAD
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
		
=======
pipeline {
    agent { label "agent1" }
    stages{
        stage("Clone Code"){
            steps{
                git url: "https://github.com/LondheShubham153/node-todo-cicd.git", branch: "master"
            }
        }
        stage("Build and Test"){
            steps{
                sh "docker build . -t node-app-test-new"
            }
        }
        stage("Push to Docker Hub"){
            steps{
                withCredentials([usernamePassword(credentialsId:"dockerHub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
                sh "docker tag node-app-test-new ${env.dockerHubUser}/node-app-test-new:latest"
                sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                sh "docker push ${env.dockerHubUser}/node-app-test-new:latest"
                }
            }
        }
        stage("Deploy"){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
    }
>>>>>>> 070756f386752cdcd1ef00668201f6c53d9962b3
}
}

