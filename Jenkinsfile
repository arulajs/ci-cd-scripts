node {
  def mvnHome = tool name: 'maven', type: 'maven'
  def npmHome = 'C:/Users/1557133/AppData/Roaming/npm'
  def build_ok = true
  
  try {
    stage('Run Development pipeline') {
    echo 'Build initiated in Development environment'
    build job: 'poc-dev-cicd-demo'
    } 
  } catch(Exception e) {
    build_ok = false
  }
  
  try {
    stage('Run Production pipeline') {
    echo 'Build initiated in Production environment'
    build job: 'poc-prod-cicd-demo'
    }
  } catch(Exception e) {
    build_ok = false
  }
  
  if(build_ok = false) {
    currentBuild.STATUS = 'FAILED'
  }
  
}
