node {
    docker.image('node:16-buster-slim').inside('-p 3000:3000') {
        stage('build') {
            sh 'npm install'
        }
        stage('test') {
            sh 'npm test -- --watch=false'
        }
    }
}