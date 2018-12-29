node {
   
   stage('Clone Source Code') { // for display purposes
      git 'https://github.com/IndumathiRanganatham/boxfuse-sample-java-war-hello.git'
         }
	stage('maven verification')
       	sh "sudo /opt/maven/apache-maven-3.6.0/bin/mvn -version"
   stage('Build') {
      // Run the maven build
      if ('true') {
         sh "sudo /opt/maven/apache-maven-3.6.0/bin/mvn -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
	 
   }
   stage('Upload to S3') {
   
   println "Here we are uploading files to S3" 
   
   }
   stage('Copy to Server') {
   sh '''
   ls -l target/
   sudo ssh -i /home/ec2-user/InduSing.pem -o StrictHostKeyChecking=no ec2-user@172.31.29.248 "ls"

   sudo scp -i /home/ec2-user/InduSing.pem target/hello*.war ec2-user@172.31.29.248:/usr/local/tomcat9/webapps/
   sudo ssh -i /home/ec2-user/InduSing.pem ec2-user@172.31.29.248 "ls -l /usr/local/tomcat9/webapps/"
   
   '''
   println "Here we are uploading files to S3" 
   
   }
   stage ('Deployment') {
   println "Deployment scripts"
   }
   
}
