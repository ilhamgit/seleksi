pipeline {
  agent any
  stages {
    stage('error') {
      steps {
        sh '''
cat /home/master/my_password.txt | sudo docker login --username 455417 --password-stdin
sudo docker tag ubuntu 455417/devops:jenkins
sudo docker push 455417/devops:jenkins


'''
      }
    }

    stage('pick') {
      steps {
        sh '''echo "apiVersion: apps/v1
kind: Deployment
metadata:
  name: jenkinstest
spec:
  selector:
    matchLabels:
      app: tes
  replicas: 1
  template:
    metadata:
      labels:
        app: tes
    spec:
      containers:
      - name: tes
        image: 455417/devops:jenkins
        ports:
        - containerPort: 80
      nodeSelector:
        role: master

---

apiVersion: v1
kind: Service
metadata:
  labels:
    app: tes
  name: jenkinstest
  namespace: default
spec:
  clusterIP: 10.97.0.25
  clusterIPs:
  - 10.97.0.25
  ports:
  - name: 80-80
    port: 80
    protocol: TCP
    targetPort: 80
  selector:
    app: tes
  type: ClusterIP" | tee bisa.yaml


'''
      }
    }

  }
  environment {
    pipeline = 'tes'
  }
}