node('master') 
{
    stage('ContinuousDownload') 
    {
      git 'https://github.com/selenium-saikrishna/maven.git'
    }
    
    stage('ContinuousBuild')
    {
        sh label: '', script: 'mvn package'
    }
 stage('ContinuousDeployment')
    {
        sh label: '', script: 'scp /var/lib/jenkins/workspace/subba_loan/webapp/target/webapp.war ubuntu@172.31.10.167:/var/lib/tomcat8/webapps/qaenv.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
        sh label: '', script: 'java -jar testing.jar'
        
    }
    stage('ContinuousDelivery')
    {
        input message: 'Waiting for Approval from Delivery Team', submitter: 'Ravi'
        sh label: '', script: 'scp /var/lib/jenkins/workspace/subba_loan/webapp/target/webapp.war ubuntu@172.31.2.144:/var/lib/tomcat8/webapps/prodenv.war'
    }
    
}
