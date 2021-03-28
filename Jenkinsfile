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
            sh "docker build -t ."

            steps {
                withDockerRegistry([url: "", Docker-ID: "dockerbuildbot-index.docker.io"]) {
                    sh("docker push jmugu/docker-tutorial")
                }
            }
        }
    }
}
