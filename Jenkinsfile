@Library("shared") _ 
pipeline{
    agent {label 'worker_node_1'}
    
    stages{
        stage("shared_library"){
            steps{
                script{
                    test()
                }
            }
        }
        stage("Git Clone") {
            steps{
                script{
                    git_clone("https://github.com/np025/django-notes-app.git","main")
                }
            }
        }
        stage("Build") {
            steps{
                script{
                    docker_build("nikki2507","nodes-app","latest")
                }
            }
        }
        stage("Push To Docker hub") {
            steps{
                echo "Pushing Image to docker hub"
                script{
                    docker_push("nodes-app","latest","nikki2507")
                }
            }
        }
        stage("Deploy") {
            steps{
                script{
                    docker_deploy()
                }
            }
        }
    }
}
