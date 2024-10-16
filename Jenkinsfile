@Library("Shared") _
pipeline {
    agent any
    
    stages {
        stage("hello"){
            steps {
                script {
                    starter()
                }
            }
        }
        stage("Code") {
            steps {
                script {
                    clone("https://github.com/pathu-1/django-notes-app.git", "main")
                }
            }
        }
        stage("Build") {
            steps {
                script {
                    docker_build("notes_app", "latest", "pathuxx")
                }
            }
        }
        stage("Test") {
            steps {
                script {
                    echo "Testing the code"
                    // Add your actual testing commands here
                }
            }
        }
        stage("Pushing Code to Docker Hub") {
            steps {
                script {
                    push_to_docker("notes-app", "latest", "pathuxx")
                }
            }
        }
        stage("Deploy") {
            steps {
                script {
                    echo "Deploying code"
                    sh "docker compose up -d"
                }
            }
        }
        // Optional Cleanup Stage
        stage("Cleanup") {
            steps {
                script {
                    echo "Cleaning up..."
                    // Add Docker cleanup commands here
                }
            }
        }
    }
}
