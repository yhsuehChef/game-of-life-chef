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
   stage('Test')
   {
       parallel(
           IntegrationTestOnJetty:
           {
               sh 'cd gameoflife-web && mvn jetty:run &'
               sleep 30
               sh 'curl localhost:9090'
               sh '(sleep 120; lsof -t -i tcp:9090 | xargs kill) &'
           },
           SonarScan:
           {   sh 'mvn sonar:sonar -Dsonar.host.url=http://localhost:9000 -Dsonar.login=48428c97f3d54d35c974dea22d2cc285bc11f8a6'
               //sh 'cd gameoflife-acceptance-tests && mvn clean verify'
           }
        )
   }
   stage('Deploy')
   {
       echo "Application can be deployed to target of choice here"
   }
}
