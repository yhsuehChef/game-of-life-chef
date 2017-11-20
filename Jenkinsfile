node('linux')
{
   currentBuild.displayName = "Game Of Life Chef Jenkinsfile"
    
   def mvnHome
   
   stage('Checkout')
   {
      mvnPath = tool 'M3.0.5-linux'
      sh 'mvn clean install'
   }
}