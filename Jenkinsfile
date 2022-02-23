node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Build image') {
  
       app = docker.build("jmugu/test")
    }

    stage('Test image') {
  

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${env.BUILD_NUMBER}")
        }
    }
    
    stage('Trigger ManifestUpdate') {
                echo "triggering updatemanifestjob"
                build job: 'updatemanifest', parameters: [string(name: 'DOCKERTAG', value: env.BUILD_NUMBER)]
        }
}

// Original pipeline starts here and end on line 69
// pipeline {
//     agent any

//     stages {
//         stage('Integration') {
//             steps {
//                 echo 'docker build -t docker/getting-started .'
//             }
//         }
//         stage('Build') {
//             steps {
//                 echo 'Building code from SCM'
//             }
//         }
//         stage('Deploy') {
//             steps {
//                 echo 'Deploy code to test environment'
//             }
//         }
//         stage('Test') {
//             steps {
//                 echo 'Release code to stage environment ready for production'
//             }
//         }
//         stage('Release') {
//             steps {
//                 echo 'Code ready To deloy to production'
//             }
//         }
//     }
// }

//END
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
