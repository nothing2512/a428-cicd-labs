node {
    docker.image('node:lts-buster-slim').inside('-p 3000:3000 -v /var/jenkins_home/workspace:/var/jenkins_home/workspace') {
        withEnv(['CI=true']) {
            stage('build') {
                sh 'npm install'
            }
            stage('test') {
                sh './jenkins/scripts/test.sh'
            }
            stage('deliver') {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
