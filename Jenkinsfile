pipeline {
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    agent {
        label 'ubuntu-1804 && amd64 && docker'
    }
    stages {
        stage('build and push') {
            when {
                branch 'master'
            }
            sh "docker build -t jmugu/scan-test:latest ."

            steps {
                withDockerRegistry([url: "", credentialsId: "dockerbuildbot-index.docker.io"]) {
                    sh("docker push jmugu/scan-test:latest")
                }
            }
        }
    }
}



// pipeline{

// 	agent any

// 	environment {
// 		DOCKERHUB_CREDENTIALS=credentials('dockerhub')
// 	}

// 	stages {
	    
// 	    stage('gitclone') {

// 			steps {
// 				git 'https://github.com/asongent/docker-tutorial.git'
// 			}
// 		}

// 		stage('Build') {

// 			steps {
// 				sh 'docker build -t jmugu/scan-test:latest .'
// 			}
// 		}

// 		stage('Login') {

// 			steps {
// 				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_PSW --password-stdin'
// 			}
// 		}

// 		stage('Push') {

// 			steps {
// 				sh 'docker push jmugu/scan-test:latest'
// 			}
// 		}
// 	}


// 	post {
// 		always {
// 			sh 'docker logout'
// 		}
// 	}
// }

// 	post {
// 		always {
// 			sh 'docker scan jmugu/scan-test'
// 		}
// 	}
