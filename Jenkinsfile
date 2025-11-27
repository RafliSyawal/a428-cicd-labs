node {
    // Ambil kode dari Git
    stage('Checkout') {
        checkout scm
    }

    // Semua build & test jalan di dalam container Node
    docker.image('node:16-buster-slim').inside('-p 3000:3000') {

        stage('Build') {
            sh 'npm install'
        }

        stage('Test') {
            // Sesuaikan dengan perintah test di package.json
            // biasanya cukup:
            sh 'npm test -- --watch=false'
            // atau kalau butuh:
            // sh 'CI=true npm test'
        }
    }
}
