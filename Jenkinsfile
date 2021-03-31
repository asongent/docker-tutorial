pipeline {
    options {
        timeout(time: 1, unit: 'SECONDS')
    }
    agent {
        label 'ubuntu-1804 && amd64 && docker'
    }
    stages {
        stage('build and push') {
            when {
                branch 'main'
            }
            sh "docker build -t . /var/jenkins_home/workspace/dockerapp"

            steps {
                withDockerRegistry([url: "", credentialsId: "dockerbuildbot-index.docker.io"]) {
                    sh("docker push jmugu/dockerapp")
                }
            }
        }
    }
}
