pipeline{
    agent any
    environment {
        PATH = "$PATH:/opt/apache-maven-3.8.5/bin"
    }
    stages{
       stage('build'){
            steps{
                sh 'mvn clean compile'
            }
         }        
       stage('test'){
            steps{
                sh 'mvn test'
            }
           stage(build){
               sh 'mvn package'
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

}
