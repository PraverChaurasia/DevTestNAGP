pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'master']], doGenerateSubmoduleConfigurations: false, 
                          extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/PraverChaurasia/DevTestNAGP.git']]])
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building.....'
                bat 'mvn clean package'
            }
        }
        
        stage('Test') {
            steps {
                echo 'Testing.....'
                bat 'mvn test'
            }
        }
       
    }
    
    post {
        success {
            echo 'Pipeline succeeded! Do any additional tasks here.'
        }
        
        failure {
            echo 'Pipeline failed! Handle failure scenarios here.'
        }
    }
}
