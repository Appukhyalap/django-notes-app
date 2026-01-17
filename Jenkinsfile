@Library("Shared") _
pipeline{
    agent { label "appu" }

    stages{
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                    clone("https://github.com/Appukhyalap/django-notes-app", "main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app", "latest", "shantaveerkhyalap")
                }
            }
        }
        stage("push to dockerHub"){
            steps{
                script{
                    docker_push("notes-app", "latest", "shantaveerkhyalap")
                }
            }
        }
        stage("Test"){
            steps{
                echo "This is testing the code"
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
		        sh "docker compose up -d"
            }
        }
    }
}
