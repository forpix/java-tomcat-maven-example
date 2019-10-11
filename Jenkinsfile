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
    
      stage('Deploy') {     
            sshagent(['663ad901-af44-4f93-803a-c841b0e8588c']) {
               sh 'scp -o StrictHostKeyChecking=no target/tomcatdeploymnetdemo.war root@192.168.43.92:/root/tomcat9/webapps'
              
          }
         
     }
      
 }
