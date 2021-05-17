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
        stage("Uploading to NExus"){
            steps{
                script{
                def pom = readMavenPom file: 'pom.xml'
               nexusArtifactUploader artifacts: [[artifactId: 'myweb', classifier: '', file: 'target/feature-1.war', type: 'war']], credentialsId: 'nexus3', groupId: 'in.javahome', nexusUrl: '172.31.31.81:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'javahome-snapshot', version: "{pom.version}"
            }
        }
        }
       stage("Deploy"){
          
           steps{
                tomcatDeploy('tomcat','ec2-user','172.31.44.101')
                echo "job completed"
               
            }
           }
       }
    }

