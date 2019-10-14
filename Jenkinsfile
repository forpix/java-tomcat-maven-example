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
            
            
            
            sshagent(['1c363da2-23b1-42c4-8567-7710f406946c']) {
                  sh '''
                 pwd
                  
                 '''
            }
    
            /*  
            sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/Tomcat-Testing/target/tomcatdeploymnetdemo.war root@10.52.109.2:/home/softwares'
              
          */
       /*sshagent(['1c363da2-23b1-42c4-8567-7710f406946c']) {
           sh 'scp -o StrictHostKeyChecking=no target/tomcatdeploymnetdemo.war root@10.52.109.2:/home/softwares' 
              
          } */
         
     }
      
 }
