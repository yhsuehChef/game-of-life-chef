// node('linux')
node
{
   currentBuild.displayName = "Game Of Life Chef Rally"
   
   stage('Build')
   {
      // mvnPath = tool 'M3.0.5-linux'
      // for Chef Rally purposes, we will assume use of the system Maven

      sh 'mvn clean install'
   }
   stage('Stage')
   {
      sh 'cd gameoflife-web && mvn jetty:run'
   }
   stage('Test')
   {
      echo 'got to Test stage'
   }  
}
