pipeline {
    
    agent any
    
    stages{
        
        stage("checkout") {
            
            steps {
                
                    git credentialsId: 'EPAM_DEMO_PERSONAL_GITHUB', branch: 'master', url: 'https://github.com/deven87/jenkinstask2.git'
                }
            
            }
        
            
        
        stage("test") {
          
            steps {
                dir('jenkinsdemo') {
            echo "testing project"
            sh 'mvn clean test'
            }
    }
            
            
        }
        
    }
    
    post {
        
        always {
            dir('jenkinsdemo') {
             echo "generating report"
             sh 'mvn surefire-report:report'
             junit '**/target/surefire-reports/*.xml'
             publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '\\target\\reports', reportFiles: 'surefire.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
             
        }
        }
        
    }
     
}
