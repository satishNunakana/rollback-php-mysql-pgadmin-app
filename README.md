# rollback-php-mysql-pgadmin-app

# pipeline script for rollback
pipeline {
    agent any
    
    stages {
        stage('Cloning Git') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/ganjivasu/phprollbackdemo.git']]])
            }
        }
        
        stage('Docker compose') {
            steps {
                sh "sudo docker-compose up -d --build"  
            }
        }     
        
    } 
        
} 
