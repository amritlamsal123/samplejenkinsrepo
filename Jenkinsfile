node('maven'){
    def mvnhome = tool name: 'maven', type: 'maven'
    stage('1st stage'){
        echo "1st  stagee"
    }
    stage('maven build'){
        sh "$mvnhome/bin/mvn clean test surefire-report:report-only"
        junit allowEmptyResults:true, testResults: 'target/surefire-reports/*.xml'
        publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'target/site', reportFiles: 'surefire-report.html', reportName: '', reportTitles: 'surefire-report.html'])
    }
    stage('maven package'){
        sh "$mvnhome/bin/mvn clean package -DskipTests=true"
    }
    stage('archieving artifacts'){
        archiveArtifacts '**/target/*.jar'
    }
 //   stage('deployment'){
     //   sshagent(['deployusr']) {
    // some block
       
      //  sh "ssh -o StrictHostKeyChecking=no ec2-user@10.0.0.53 /opt/tomcat/start.sh"
      //  sh "scp -o StrictHostKeyChecking=no /home/ec2-user/workspace/pipeline/target/my-app-1-RELEASE.jar ec2-user@10.0.0.53:/opt/tomcat/webapp"
      //  sh "ssh -o StrictHostKeyChecking=no ec2-user@10.0.0.53 /opt/tomcat/stop.sh"
  //  }
    }
}
