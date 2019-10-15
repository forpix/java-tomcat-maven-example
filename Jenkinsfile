node{
      def mvnHome = tool name: 'maven 3.5.4', type: 'maven' 
      stage('Checkout'){
         git 'https://github.com/forpix/java-tomcat-maven-example'
      }  
      stage('Build'){
         //// Get maven home path and build
        sh "${mvnHome}/bin/mvn clean package -Dmaven.test.skip=true";pwd
      }
     stage ('Test-JUnit'){
         sh "'${mvnHome}/bin/mvn' test surefire-report:report"
      }  
      stage ('Deploy') {
         sh 'scp -o StrictHostKeyChecking=no target/tomcatdeploymnetdemo.war root@10.52.109.2:/home/softwares/tomcat9/webapps'
      }
}
