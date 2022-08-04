pipeline {
  agent any
  stages {
    stage('error') {
      steps {
        sh '''
cat /home/master/my_password.txt | sudo docker login --username 455417 --password-stdin
docker tag ubuntu 455417/devops:jenkins
docker push 455417/devops:jenkins


'''
      }
    }

  }
  environment {
    pipeline = 'tes'
  }
}