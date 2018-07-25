pipeline {
    agent any
    stages{
        stage ("App build"){
            steps {
                script {
                    sh "npm install"
                    sh "npm run build"                
                }
            }
        }
        stage ("docker build"){
            steps {
                script {
                    sh "sudo docker build -t testdemo:$BUILD_NUMBER ."
                    sh "sudo docker tag testdemo:$BUILD_NUMBER hsafir/testdemo:$BUILD_NUMBER"
                    sh "sudo docker push hsafir/testdemo:$BUILD_NUMBER"
                }
            }
        }
        stage ("Deploy to openshift"){
            steps {
                script {
                     sh "/usr/bin/oc-tool/oc --server https://192.168.99.100:8443 --token=ISvTOZiU2SyKc6a2GjO0DvbVBKWAC2VlG60zpD8rc9g new-app hsafir/testdemo:$BUILD_NUMBER"
                }
            }
        }
    }
}
