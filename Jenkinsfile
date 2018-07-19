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
    }
}
