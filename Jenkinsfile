node {
    stage('Checkout') {
        // Ambil source code dari Git (branch react-app)
        checkout scm
    }

    stage('Build in Docker') {
        docker.image('node:16-buster-slim').inside('-p 3000:3000') {
            sh 'npm install'
            // nanti kalau mau, bisa lanjut:
            // sh 'npm test'
            // sh 'npm run build'
        }
    }
}
