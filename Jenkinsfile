pipeline
{

   agent
   {
     node
     {
        label 'maven'
     }
   }

   stages
   {
     stage("build")
     {
       steps 
       {
        sh 'mvn clean deploy -Dmaven.test.skip=true'
       }
     }

    stage('SonarQube analysis') {
    environment {
      scannerHome = tool 'sonarqube-scanner'
    }
    steps{
    withSonarQubeEnv('sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner"
    }
    }
  }

   }


}
