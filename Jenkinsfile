@Library("Shared") _
pipeline{
    
    agent{label "vinod"}
    
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
                    clone("https://github.com/Jayasuryanarayana/django-notes-app.git","dev")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app","latest","jayasuryanarayana")
                }
                echo"built successfull"
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","jayasuryanarayana")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is Deploying the code"
                sh"docker compose down && docker compose up -d"
            }
        }
    }
}
