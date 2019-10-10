node {
  def mvnHome = tool name: 'maven', type: 'maven'
  def npmHome = 'C:/Users/1557133/AppData/Roaming/npm'
  def build_ok = true
  
  stage('Run Development pipeline') {
    echo 'Build initiated in Development environment'
    build job: 'poc-dev-cicd-demo'
  }
  
  if(currentBuild.result == "SUCCESS")
  {
    stage('Run Production pipeline') {
    echo 'Build initiated in Production environment'
    build job: 'poc-prod-cicd-demo'
  }
  }
  
}
