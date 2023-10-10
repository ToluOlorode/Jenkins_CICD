pipeline {
    agent any

 tools {
        jdk "jdk17"
        maven "maven"
    }
    
     environment {
        SCANNER_HOME=tool 'sonar-scanner'
    }


    stages {
        stage('Git Checkout'){
            steps{
                 git branch: 'main', url: 'https://github.com/ToluOlorode/spring-petclinic.git'
            }

        }
        
        stage('Compile') {
         steps {
                sh "mvn compile"
     }
    }
    
     stage('Test'){
            steps {
                sh "mvn test"
        }
    }
    
    stage('Code Quality Analysis') {
    steps {
        script {
            withSonarQubeEnv('sonar-server') {
                sh """$SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=petclinic \
                    -Dsonar.java.binaries=. \
                    -Dsonar.projectKey=petclinic """
            }
        }
    }
}
    
        stage('Build'){
            steps {
                sh "mvn clean install"
            }
        }
        
        stage('Manual Approval'){
            steps {
                input message: 'Do you want to proceed to Deployment?', ok: 'Proceed'
            }
        }
        
         stage('Deploy to Server') {
            steps {
              // Be sure to change user@nginx-server otherwise the build won't work
                sh "rsync -avz --delete ./dist/* user@nginx-server:/var/www/html/petclinic"
                }
            }

    }
}
