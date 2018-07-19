pipeline {
    agent any /*where to run the code? any node can run*/
stages{
        stage('Build'){
            steps {
                /*shell execute*/
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}
