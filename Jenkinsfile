pipeline {
    agent any 
    
    stages {
        
        
        stage('Cleanup') {
            steps {
                sh 'rm -rf taxi-booking'  // Delete old project
            }
        }
        
        stage('Print') {
            steps {
                echo 'new project'
            }
        }
        
        stage('Clone') {
            steps {
                sh 'git clone -b dev https://github.com/reddi122/taxi-booking.git'
            }
        }
        
        
        
        stage('Build') {
            steps {
                dir("taxi-booking") { // Ensure build runs inside the cloned project
                    sh 'mvn clean package'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                sh 'cp taxi-booking/taxi-booking/target/*.war /opt/tomcat/webapps/'
            }
        }

    }
}
