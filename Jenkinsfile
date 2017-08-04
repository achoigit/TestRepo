node {
  stage('Checkout') {
    checkout scm    
  }
  stage('Build') {
    app = docker.build("andychoi20170803/testrepo")
  }
  stage('Test') {
    docker.image("andychoi20170803/testrepo").withRun("-it -p 8000:8001") {c ->
      sh 'curl -f http://127.0.0.1:8001'
    }
  }
  stage('Push') {
    docker.withRegistry('https://registry.hub.docker.com','docker-hub-credentials') {
      app.push("${env.BUILD_NUMBER}")
      app.push("latest")
    }
  }
}
