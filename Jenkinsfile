node {
  def mvnHome = tool name: 'maven', type: 'maven'
  def npmHome = 'C:/Users/1557133/AppData/Roaming/npm'
  def build_ok = true
  
  try {
    stage('Run Development pipeline') {
    echo 'Build initiated in Development environment'
    build job: 'poc-dev-cicd-demo'
    } 
  } catch(e) {
    build_ok = false
  }
  
  stage('Publish Development Report') {
    publishHTML([allowMissing: false, alwaysLinkToLastBuild: true, keepAll: true, reportDir: 'C:\\Users\\1557133\\.jenkins\\workspace\\poc-dev-cicd-demo\\newman', reportFiles: 'devtest-report.html', reportName: 'TestReport-Dev', reportTitles: 'TestReport-Dev'])
     echo 'Test report generated'
    }
  
  if(build_ok) {
    try {
    stage('Run Production pipeline') {
    echo 'Build initiated in Production environment'
    build job: 'poc-prod-cicd-demo'
    }
  } catch(e) {
    build_ok = false
  }
  }
  
  stage('Publish Production Report') {
    publishHTML([allowMissing: false, alwaysLinkToLastBuild: true, keepAll: true, reportDir: 'C:\\Users\\1557133\\.jenkins\\workspace\\poc-prod-cicd-demo\\newman', reportFiles: 'prodtest-report.html', reportName: 'TestReport-Prod', reportTitles: 'TestReport-Prod'])
     echo 'Test report generated'
    }
  
  if(build_ok) {
        currentBuild.result = "SUCCESS"
    } else {
        currentBuild.result = "FAILURE"
    }
  
}
