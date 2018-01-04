node('linux')
{
   currentBuild.displayName = "Game Of Life Chef Rally"
   
   stage('SCM Checkout')
   {
      git 'https://github.com/yhsuehChef/game-of-life-chef.git'
   }
   stage('Build')
   {
      // mvnPath = tool 'M3.0.5-linux'
      // for Chef Rally purposes, we will assume use of the system Maven

      sh 'mvn clean install'
   }
   stage('Test Deployment')
   {
       parallel(
           AcceptanceTest:
           {
               sh 'cd gameoflife-acceptance-tests && mvn clean verify'
           },
           DeployToUAT:
           {
               sh 'cd gameoflife-web && mvn jetty:run'
           }
        )
   }
}
