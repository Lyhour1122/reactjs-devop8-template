pipeline {
    agent any

    stages {
        stage("Build"){
            steps{
                sh """
                    docker build -t jenkins-react-pipeline . 
                """
            }
        }


        stage("Deploy"){
            steps{
                sh"""
                
                docker stop reactjs-cont || true 
                docker rm reactjs-cont || true 
                
                docker run -dp 3000:80 \
                    --name reactjs-cont \
                    jenkins-react-pipeline
                """

            }
        }
        stage("Check Files") {
        steps {
        sh 'ls -al'
         }
        }
        
    }
}
