pipeline {
    agent any 
    tools { 
        maven 'maven'
    }
    stages {
        stage("Clean up") {
            steps {
                deleteDir()
            }
        }
        stage("Clone repo") {
            steps {
                sh "git clone https://github.com/SalehEddineBG/tp4jenkins.git"
            }
        }
        stage("Generate backend image") {
            steps {
                dir("tp4jenkins/springboot/app") {
                    sh "mvn clean install"
                    sh "docker build -t backend ."
                }                
            }
        }
        stage('Generate Frontend image') {
            steps {
                dir('tp4jenkins/angular-app') {
                    sh 'docker build -t frontend .'
                }
            }
        }
        stage("Run docker compose") {
            steps {
                dir("tp4jenkins") {
                    sh "docker-compose up -d"
                }                
            }
        }
    }
}

