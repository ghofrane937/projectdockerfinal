node {
   stage('Prepare') {
      
      git credentialsId: 'git-cred', url: 'https://github.com/ghofrane937/projectdockerfinal.git'
      if (!fileExists("docker-compose.yml")) {
         error('Docker compose missing.')
      }
   }
   
     
   stage('Test') {
            agent {
                docker {
                    image 'python:3.8-slim-buster'
                }
            }
            steps {
                sh 'pip install flask && pip install xmlrunner'
                sh 'python app/unittests.py'
            }
            post {
                always {
                    junit 'test-reports/results.xml'
                }
            }
