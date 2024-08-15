/*pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}*/

node{
    def app 
    stage('clone repository'){
        checkout scm
    }
    stage('Build image'){
        app = docker.build("aravind5260/aravind_repository_1")
    }
    stage('Test image'){
        app.inside{
            sh 'echo "Tests passed"'
        }
    }

    stqage('Push image){
        docker.withRegistry('https://registry.hub.docker.com','docker-hub-credentials'){
                    app.push("${env,BUILD_NUMBER}")
                    app.push("latest")
        }
        }
    }
