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

            stage('Deploy to Production') {
                steps {
                    /*it will fail if in 5 days no one approve/disapprove*/
                    timeout(time: 5, unit: 'DAYS') {
                        input message: 'Approve Production Deployment?'
                    }

                    build job: 'deploy-to-prod'
                }
                 post {
                     success {
                        echo 'Code deployed to prod'
                     }

                     failure {
                        /*or send email*/
                        echo 'Prod deployment failed'
                     }
                 }
            }
    }
}
