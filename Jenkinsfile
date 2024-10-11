pipeline {
    agent any
    
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/chiru1se/saidemytrend.git'
            }
        }
    
        stage('Build') {
            steps {
                echo "----------Build Started----------"
                sh 'mvn clean deploy'
                echo "----------Build Completed----------"
            }
        }
        
        stage('SonarQube Analysis') {
            environment {
                scannerHome = tool 'saidemy-sonar-scanner'
            }
            steps {
                withSonarQubeEnv(saidemy-sonar-scanner){
                    sh "${scannerHome}/bin/sonar-scanner"
                }    
            }
        }
    }
}

