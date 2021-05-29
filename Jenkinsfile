pipeline {
    agent any
    stages {
        stage('Retrieve image from registry') {
            steps {
                
            }
        }
        stage('Deploy image into Kubernetes cluster') {
            steps {
                
            }
        }
        stage('Run start scripts for app') {
            steps {
                
            }
        }
        stage('Run performance tests') {
            steps {
                
            }
        }
    }
     post { 
        always { 
            echo 'Jenkins finished'
            deleteDir() /* clean up the workspace */
        }
         success {
            echo 'Build succeeded'
        }
        unstable {
            echo 'Build unstable'
            echo 'Build unstable. Please fix.'
            mail to: 'de.koenigthilo@gmail.com',
             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
             body: "Something is wrong with ${env.BUILD_URL}"
        }
        failure {
            echo 'Build failed. Please fix.'
            mail to: 'de.koenigthilo@gmail.com',
             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
             body: "Something is wrong with ${env.BUILD_URL}"
        }
    }
}