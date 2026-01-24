@Library("shared") _
pipeline{
    agent {label "vinod"}
    stages {
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("code"){
            steps{
                script{
                clone("https://github.com/9Bhavana/django-notes-app.git", "main")
                }
            }
        }
         stage("Build"){
            steps{
                script{
                docker_build("notes-app", "latest", "bhanu40")
                }
            }
        }
         stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app", "latest", "bhanu40")
                }
            }
        }
         stage("Deploy"){
            steps{
                echo "this is Deploying the code"
                sh "docker compose up -d"
            }
        }
    }
}
