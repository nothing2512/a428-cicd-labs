Node {
    docker.image('node:lts-buster-slim').inside(''-p 3000:3000'') {
        withEnv(['CI=true']) {
            stage('build') {
                sh 'npm install'
            }
            stage('Test') {
                sh './jenkins/scripts/test.sh'
            }
            stage('Deliver') {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
