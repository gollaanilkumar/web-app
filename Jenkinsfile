pipeline{
    agent any
      tools {
        maven 'maven3' 
    }
    stages{
        stage("SCM"){
            steps{
                echo "hi am commenting thr SCM becuase it is twice"
               // git branch: 'feature-1', url: 'https://github.com/gollaanilkumar/web-app'
            }
        }
        stage("BUild"){
            steps{
                sh 'mvn clean package'
                sh 'mv target/my*.war   target/feature-1.war'
            }
        }
       stage("Deploy"){
           steps{
               sshagent(['tomcat']) {
                    //rename war
                    sh 'mv target/feature-1.war target/anil.war'
                    //deploy war file to tomcat
                    sh 'scp -o StrictHostKeyChecking=no target/anil.war ec2-user@172.31.44.101:/opt/tomcat8/webapps'
                    // start and restart tomcat
                    
                    sh 'ssh ec2-user@172.31.44.101 /opt/tomcat8/bin/shutdown.sh'
                    sh 'ssh ec2-user@172.31.44.101 /opt/tomcat8/bin/startup.sh'
                    
                    
    // some block
}
           }
       }
    }
}
