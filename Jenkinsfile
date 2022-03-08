node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner'
    withSonarQubeEnv() {
      bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll begin /k:\"jenkinsSAST\""
      bat "dotnet build"
      bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll end"
    }
  }
}
