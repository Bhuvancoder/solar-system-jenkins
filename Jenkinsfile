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
        stage('Dependency Scanning'){
            parallel{
                stage('NPM dependency Audit'){
                    steps{
                        bat 'npm audit --audit-level=critical'
                    }
                }
                stage('OWASP dependency Check'){
                   steps { 
                    dependencyCheck additionalArguments: '', 
                        odcInstallation: 'OWASP-DependencyCheck-10', 
                        outdir: 'dependency-check-report', 
                        scanpath: '.', 
                        format: 'ALL'
                }
            }
        }  
    }
}