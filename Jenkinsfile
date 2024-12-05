@Library("Shared") _
pipeline{ 
    
    agent {label "newagent"}
    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        
        stage("Code"){
            steps{
                script{
                    clone("https://github.com/devopsguru-debug/djangoapp.git", "master")
                    
                }
            }
        }
        
        stage("Build"){
            steps{
                script{
                    docker_build("notes","latest","sahilbonami")
                }
            }
        }
        
        stage("Push"){
            steps{
                script{
                    docker_push("notes","latest","sahilbonami")
                }
            }
        }
        
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker run -d -p 8000:8000 notes:latest"
            }
        }
    }
}
