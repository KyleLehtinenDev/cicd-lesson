pipeline {
    agent { docker { image 'cicd-lesson' } }
    stages {
        stage('build') {
            steps {
                sh 'echo "hello world"'
            }
        }
    }
}
