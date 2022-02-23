pipeline {
     agent any
     stages {
    
         stage('Clone Repo') {
           steps {
             sh 'git clone https://github.com/harshitha423/repo4.git
             }
         }

         stage('Build Docker Image') {
           steps {
             sh 'cd /var/lib/jenkins/workspace/pipeline2/repo4'
             sh ' cp /var/lib/jenkins/workspace/pipeline2/repo4/* /var/lib/jenkins/workspace/repo4'
             sh 'docker build -t 423445/nginx:v1 .'
             }
         }

         stage('Push Image to Docker Hub') {
           steps {
             sh 'docker -H tcp://ip-172-31-41-0:2375 run --rm -dit --name webapp1 --hostname webapp1 -p 4000:80 423445/nginx:v1'
             }
         }

         Stage('Check Webapp Reachability') {
           steps {
             sh 'sleep 10s'
             sh 'curl http://ec2-35-154-189-184.ap-south-1.compute.amazonaws.com:4000'
             }
         }
       
     }
 }
