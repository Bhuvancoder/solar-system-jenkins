pipeline{
    agent any
    tools {
        nodejs 'NodeJs-24.11.1'
    }
    stages{
        stage('node version'){
            steps{
                bat 'node -v'
                bat 'npm -v'
            }
        }
    }
}