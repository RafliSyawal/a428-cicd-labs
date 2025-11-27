node {
    stage('Checkout') {
        checkout scm
    }

    // Semua build & test jalan di dalam container Node
    docker.image('node:16-buster-slim').inside('-p 3000:3000') {

        stage('Build') {
            sh 'npm install'
        }

        stage('Test') {
            sh 'npm test -- --watch=false'
        }
        stage('Deploy') {
            sh './jenkins/scripts/deliver.sh'
            input_message: "Sudah selesai menggunakan react app? (Klik "proceed" untuk mengakhiri)"
            sh './jenkins/scripts/kill.sh'
        }
    }
}
