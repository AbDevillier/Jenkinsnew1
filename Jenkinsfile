pipeline {
  agent any
  
  stages {
    stage('Build') {
      steps {
        // Checkout the source code
        git 'https://github.com/AbDevillier/Jenkinsnew1.git'
        
        // Build the application
        sh './gradlew build'
      }
    }
    
    stage('Test') {
      steps {
        // Run unit tests
        sh './gradlew test'
        
        // Run integration tests
        sh './gradlew integrationTest'
      }
    }
    
    stage('Deploy') {
      steps {
        // Deploy the application
        sh 'kubectl apply -f deployment.yaml'
        
        // Wait for deployment to complete
        sh 'kubectl rollout status deployment/my-app'
        
        // Verify the deployment
        sh 'curl http://my-app:8080'
      }
    }
  }
}
