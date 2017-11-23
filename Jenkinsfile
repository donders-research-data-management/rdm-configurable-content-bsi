node {
    def mvnHome = tool 'M3'
    try {
        stage('Checkout') {
            checkout scm
        }

        stage('Build') {
            sh 'echo "Git hash: `git rev-parse --verify HEAD` , Build on `date`" > build.txt'
            sh "make dist"
        }

        stage('Maven deploy') {
            sh "${mvnHome}/bin/mvn -U clean deploy"
        }

        stage('Archive') {
            archiveArtifacts artifacts: 'target/rdm-ontology-*', fingerprint: true
        }
    } finally {
        deleteDir()
    }
}