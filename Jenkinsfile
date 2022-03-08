node {
  stage('SCM') {
    checkout scm
  }
  sonar.analysis.mode=publish
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner'
    withSonarQubeEnv() {
     
      bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll begin /k:\"jenkinsSAST\""
      bat "dotnet build"
      bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll end"
    }
  }
}
