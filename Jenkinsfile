pipeline {
    agent any
    stages{
        stage ("test demo"){
            steps {
                script {
                    sh "npm install"
                    sh "npm run build"
                    sh "sudo docker build -t testdemo:$BUILD_NUMBER ."
                   // sh "docker stop \$(docker ps -aq)"
                   // sh "docker rm \$(docker ps -aq)"
                    sh "sudo docker run -i -t -p 80:80 testdemo:$BUILD_NUMBER"
                }
            }
        }
    }
}
