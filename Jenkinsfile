// node('linux')
node
{
   currentBuild.displayName = "Game Of Life Chef - using Jenkinsfile"
    
   // def mvnHome
   
   stage('Checkout')
   {
      // mvnPath = tool 'M3.0.5-linux'
      sh 'mvn clean install'
   }
}
