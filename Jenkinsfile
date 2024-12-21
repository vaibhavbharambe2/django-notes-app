@Library("PushImage") _
pipeline{
    
    agent { label 'sham' }
    
    stages{
        
        stage("Code"){
            steps{
                script{
                clone("https://github.com/vaibhavbharambe2/django-notes-app.git", "main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    build("notes-app","latest","vaibhav237")
                }
            }
        }
        stage("Push"){
            steps{
                script{
			        PushImage("notes-app","latest","vaibhav237")  
		        }
            }
        }
        stage("Depoly"){
            steps{
                echo "Deploying the code and executing application"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
