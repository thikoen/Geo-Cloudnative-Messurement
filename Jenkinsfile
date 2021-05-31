pipeline {
   
    agent any
    
    parameters {
        choice(name: 'Mode', choices: ['Deploy + Test', 'Deploy', 'Test'], description: 'Deploys current Version and tests den Performance or just deploys or tests it.')
    }

   /*
    environment {       
        registry = "thkoenia/wahlprojekt:05"   
    }
   */

    stages {
       
        stage('Deploy image into Kubernetes cluster') {
           steps {
               script {
                   if(params.Mode != 'Test'){
                       echo 'Retrieve image from registry'
                       sh "sudo kubectl apply -f geo-deployment.yaml"
                   }
               }
                
            }
        }
        
        stage('Run start scripts for app') {
            steps {
                script {
                  // String currentPod = sh(script: 'sudo kubectl get pods -o=name', returnStdout: true).trim()
                  // sh "echo Injecting test data in $currentPod"
                  // sh "sudo kubectl exec -t $currentPod -- npm run seed"
                  sh "sudo kubectl exec -t $currentPod -- npm start && exit"
                }
            }
        }

        stage('Run performance tests') {
            steps {
                echo 'Deploy image into Kubernetes cluster'
            }
        }
    }
   /* 
     post {
        
        always { 
            echo 'Jenkins finished'
            deleteDir()
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
    
    */
}
