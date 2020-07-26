pipeline {
    agent any
    


    triggers {
         pollSCM('* * * * *') // Polling Source Control
     }

stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage ('Deployments'){
            
                stage ('Deploy to Staging'){
                    steps {
                        sh "cp  **/target/*.war /Applications/apache-tomcat-9.0.37/webapps"
                    }
                }

           
            
        }
    }
}