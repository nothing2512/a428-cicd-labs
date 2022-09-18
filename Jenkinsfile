node {
    docker.image('node:16').inside('-p 3000:3000') {
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
