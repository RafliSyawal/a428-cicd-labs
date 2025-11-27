node {
    stage('Checkout') {
        checkout scm
    }

    // Semua build & test jalan di dalam container Node
    docker.image('node:16-buster-slim').inside('-p 3000:3000') {

        stage ('fix permissions') {
            sh 'chmod +x ./jenkins/scripts/*.sh'
        }

        stage('Build') {
            sh 'npm install'
        }

        stage('Test') {
            sh './jenkins/scripts/test.sh'
            sh 'npm test -- --watch=false'
        }
        stage('Deploy') {
            // build & jalankan React
            sh './jenkins/scripts/deliver.sh'

            // PAUSE sampai kamu klik "Proceed" di Jenkins
            input message: 'Sudah selesai menggunakan react app? (Klik "Proceed" untuk mengakhiri pipeline)'

            // matikan app setelah kamu klik Proceed
            sh './jenkins/scripts/kill.sh'
        }
    }
}
