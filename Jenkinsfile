@Library('sharedlibs') _

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
                tomcat-deploy("tomcat","ec2-user",172.31.44.101)
    // some block
}
           }
       }
    }
}
