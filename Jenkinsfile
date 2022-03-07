node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    bat "dotnet tool install --global dotnet-sonarscanner --version 4.3.1"
    def scannerHome = tool 'SonarScanner for MSBuild'
    withSonarQubeEnv() {
      bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll begin /k:\"jenkinsSAST\" /d:sonar.verbose=true"
      bat "dotnet build"
      bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll end"
    }
  }
}
