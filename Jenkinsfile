pipeline {
  
  agent any
    
  tools {
    nodejs "Node"
  }
    
  stages {
    
    stage('Build Jar') {
        steps {
           script {
             echo "Building Jar File"
             sh 'npm install -g'
            }
        }
    }  
    stage('Build Docker Image and Push') {
        steps {
            script {
                echo "Building the Docker image..."
                withCredentials([usernamePassword(credentialsId: 'docker-hub-repo', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                sh 'docker build -t thejeshkumar/react-js:1.0 .'
                sh "echo $PASS | docker login -u $USER --password-stdin"
                sh 'docker push thejeshkumar/react-js:1.0'
               }
            }
        }
    }
  }
}
