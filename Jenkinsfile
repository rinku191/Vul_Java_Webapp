pipeline
{
agent any
  tools{
  maven "Maven"
  }
  stages{
    stage("Initialize"){
      steps{
      sh """
      echo "PATH = ${PATH}"
      echo "M2_Home = ${M2_Home}"
      """
      }
    }
    stage("Build"){
      steps{
      sh "mvn clean package"
      }
    }
    stage("Deploy-To-Tomcat"){
    steps{
    sshagent(["Tomcat"])
      {
     sh 'scp -o StrictHostKeyChecking=no /target/*.war kali@192.168.25.131:~/Desktop/prod/apache-tomcat-9.0.70/webapps/webapp.war'
      }
    }
  } 
}
}
  
