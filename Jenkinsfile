@Library("Shared") _
pipeline {
    agent { label 'Sameer' }

    stages {

        stage("hello") {
            steps {
                script {
                    hello()
                }
            }
        }
stage("Cloning") { 
            steps {        
                 script{      
                clone('https://github.com/thawaresameer715-cyber/django-notes-app-preTested.git','main') 
                   } 
            }
        }
        stage('build') {
            steps {
                script {
                    docker_build("notes-app", "latest", "sameerthaware")
                }
            }
        }

        stage("push to dockerhub") {
            steps {
                script {
                    docker_push("notes-app", "latest", "sameerthaware")
                }
            }
        }

        stage('deploying') {
            steps {
                echo "deploying"
                sh "docker-compose up -d"
            }
        }
    }
}

