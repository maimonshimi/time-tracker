node {
   def mvnHome
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/zivkashtan/course'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'M3'
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
 stage('Creating Dockerfile') {
       //Create the Dockerfile in the workdir
    sh '‘tomcat:8.0.20-jre8’ > Dockerfile'
    sh '\'COPY ./web/target/time-tracker-web-0.3.1.war /usr/local/tomcat/webapps/\' >> Dockerfile'
    
     
 }
    
    
    
    
    
}
