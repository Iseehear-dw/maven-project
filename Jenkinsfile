pipeline {
    agent any

    stages{
            stage('Build'){
                steps {
                    /* sh 'mvn clean package' */
                    bat 'mvn clean package'
                }
                post {
                    success {
                        echo 'Now Archiving...'
                        archiveArtifacts artifacts: '**/target/*.war'
                    }
                }
            }

            stage('Deploy to Staging') {
                steps {
                    /*this is the project name, we created in jenkins web ui*/
                    build job: 'deploy-to-staging'
                }
            }
    }
}
