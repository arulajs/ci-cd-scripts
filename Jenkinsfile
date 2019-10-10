node {
  def mvnHome = tool name: 'maven', type: 'maven'
  def npmHome = 'C:/Users/1557133/AppData/Roaming/npm'
  def build_ok = true
  
  stage('SCM Checkout') {
    git credentialsId: 'a52c80ba-af84-413f-aff3-01a35f1fa767', url: 'https://github.com/arulajs/poc-emi-management.git'
    echo 'SCM Checkout is successful'
  }
  
  stage('Compile-Package') {
    bat "${mvnHome}/bin/mvn package"
    echo 'Compile-Package is successful'
  }
  
  stage('Code Review') { 
    echo 'Code review development is in progress'
  }
  
  stage('Deploy to Server') { 
     echo 'Deployment start soon'
    }
  
  stage('SCM Postman-Collection Checkout') { 
    git credentialsId: 'a52c80ba-af84-413f-aff3-01a35f1fa767', url: 'https://github.com/arulajs/Postman-Collection.git'
     echo 'Postman-Collection checkout is complete'
    }
  try {
  stage('Postman-Collection Run') { 
    bat "newman run EMICollection.postman_collection -r cli,html --reporter-html-export \"newman/test-report.html\""
     echo 'Test is complete'
    } 
  } catch(e) {
        build_ok = false
        echo e.toString()  
    }
  
  stage('Test Report') {
    publishHTML([allowMissing: false, alwaysLinkToLastBuild: true, keepAll: false, reportDir: 'newman', reportFiles: 'test-report.html', reportName: 'HTML Report', reportTitles: ''])
     echo 'Report generated'
    }
  
  if(build_ok) {
        currentBuild.result = "SUCCESS"
    } else {
        currentBuild.result = "FAILURE"
    }
}
