pipeline {
    stages {
        stage('hello')
            steps {
                sh 'echo "hello"'
            }
        stage('build') {
            steps {
                sh 'pip install flask'
            }
        }
        stage('test') {
            steps {
                sh 'python test.py'
            }
            post {
                always {junit 'test-reports/*.xml'}
            }
        }
    }
}
