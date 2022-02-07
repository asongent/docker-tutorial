pipeline {
    agent any

    stages {
        stage('Integration') {
            steps {
                sh 'docker build -t docker/getting-started .'
'
            }
        }
        stage('Build') {
            steps {
                echo 'Building code from SCM'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploy code to test environment'
            }
        }
        stage('Test') {
            steps {
                echo 'Release code to stage environment ready for production'
            }
        }
        stage('Release') {
            steps {
                echo 'Code ready To deloy to production'
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
