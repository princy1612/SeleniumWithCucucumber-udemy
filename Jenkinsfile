node('master') {
    stage('check out') {
 git credentialsId: '911c2672-2096-4046-9317-a31226659fbc', url: 'https://github.com/princy1612/SeleniumWithCucucumber-udemy.git'
}
     stage ("build")
    {
        echo("build the  code")
       bat 'mvn verify'
      // powershell 'mvn verify'
      // maven'mvn verify'
    }
stage('report'){

cucumber failedFeaturesNumber: -1, failedScenariosNumber: -1, failedStepsNumber: -1, fileIncludePattern: '**/*.json', jsonReportDirectory: 'target', pendingStepsNumber: -1, skippedStepsNumber: -1, sortingMethod: 'ALPHABETICAL', undefinedStepsNumber: -1
}
   stage('Smoke') {
        
            publishHTML (target: [
                    reportDir: 'target/site/cucumber-pretty',
                    reportFiles: 'index.html',
                    reportName: "Smoke tests report"
            ])
    
    }
    stage('API') {
       
            publishHTML (target: [
                    reportDir: 'target/site/cucumber-pretty',
                    reportFiles: 'index.html',
                    reportName: "API tests report"
            ])
    }
    stage('UI') {
      
            publishHTML (target: [
                    reportDir: 'target/site/cucumber-pretty',
                    reportFiles: 'index.html',
                    reportName: "UI tests report"
            ])
    }

stage('mail')
{
 
emailext body: 'build+test_report  is completed ', subject: 'testing the project', to: 'princymarina1612@gamil.com'
}
}
