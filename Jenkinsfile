pipeline{
    agent any
    tools {
        nodejs 'NodeJs-24.11.1'
    }
    stages{
        stage('Installing dependencies'){
            steps{
                bat 'npm install --no-audit'
            }
        }
        stage('NPM dependency Audit'){
            steps{
                bat 'npm audit --audit-level=critical'
            }
        }
        stage('OWASP dependency Check'){
            steps{
                dependencyCheck additionalArguments: '''--scan \\\'./\\\'
                    --out \\\'./\\\'
                    --format \\\'ALL\\\'
                    --prettyPrint''', odcInstallation: 'OWASP-DependencyCheck-10'
            }
        }
    }
}