pipeline{
    agent any
    environment {
        PATH = "$PATH:/opt/apache-maven-3.8.5/bin"
    }
    stages{
       stage('GetCode'){
            steps{
                git 'https://github.com/satheeshmskr/web-app.git'
            }
         }        
       stage('Build'){
            steps{
                sh 'mvn compile package'
            }
         }
        stage('SonarQube analysis') {
//    def scannerHome = tool 'Sonar-Scanner';
        steps{
        withSonarQubeEnv('sonarqube') { 
        // If you have configured more than one global server connection, you can specify its name
//    //  sh "${scannerHome}/bin/sonar-scanner"
        sh "mvn sonar:sonar"
    }
        }
        }
       
    }
}
