node ('master') {
  checkout scm
  stage('Build') {
    withMaven(maven: 'M3') {
      if (isUnix()) {
        sh '_JAVA_OPTIONS=-Djdk.net.URLClassPath.disableClassPathURLCheck=true mvn -Dmaven.test.failure.ignore clean package'
      }
      else {
        bat 'mvn -Dmaven.test.failure.ignore clean package'
      }
    }
  }
  stage('Results') {
    junit '**/target/surefire-reports/TEST-*.xml'
    archive 'target/*.jar'
  }
}
