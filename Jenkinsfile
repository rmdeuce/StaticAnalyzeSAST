node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarScanner for MSBuild'
    withSonarQubeEnv() {
      bat "dotnet tool install --global dotnet-sonarscanner --version 4.8.0"
      bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll begin /k:\"jenkinsSAST\" /d:sonar.verbose=true"
      bat "dotnet build"
      bat "dotnet ${scannerHome}\\SonarScanner.MSBuild.dll end"
    }
  }
}
