node('maven'){
    def mvnhome = tool name: 'maven360', type: 'maven'
    stage('1st stage'){
        echo "1st  stage"
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
}
