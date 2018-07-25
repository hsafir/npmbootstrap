pipeline {
    agent any
    stages{
        stage ("test demo"){
            steps {
                script {
                    sh "npm install"
                    sh "npm run build"
                    sh "sudo docker build -t testdemo:$BUILD_NUMBER ."
                    sh "sudo docker stop \$(docker ps -q)"
                   // sh "sudo docker rm \$(docker ps -aq)"
                    sh "sudo docker run -d -p 80:80 testdemo:$BUILD_NUMBER"
                }
            }
        }
    }
}
