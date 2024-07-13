pipeline {
agent any
stages {
stage ('Checkout') {
steps {

git branch:'master', url: 'https://github.com/OWASP/Vulnerable-Web-
Application.git'

}
}
stage('Code Quality Check via SonarQube') {
steps {
script {
def scannerHome = tool 'SonarQube';
withSonarQubeEnv('SonarQube') {
sh "/var/jenkins_home/tools/hudson.plugins.sonar.SonarRunnerInstallation/SonarQube/bin/sonar-scanner -Dsonar.projectKey=OWASP -Dsonar.sources=. -Dsonar.host.url=http://192.168.1.10:9000 -Dsonar.token=sqp_253565ca4866578cf77f8b41f1078ecf2cc5545b"
}
}
}
}
}
post {
always {
recordIssues enabledForFailure: true, tool: sonarQube()
}
}
}