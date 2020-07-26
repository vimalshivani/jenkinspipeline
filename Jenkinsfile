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
            parallel{
                stage ('Deploy to Staging'){
                    steps {
                        sh "cp -i  **/target/*.war /Applications/apache-tomcat-9.0.37/webapps"
                    }
                }

                stage ("Deploy to Production"){
                    steps {
                        sh "cp -i  **/target/*.war /Applications/apache-tomcat-9.0.37/webapps"
                    }
                }
            }
        }
    }
}