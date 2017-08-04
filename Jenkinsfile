node {
  stage('Checkout') {
    checkout scm    
  }
  stage('Build') {
    app = docker.build("andychoi20170803/testrepo")
  }
  stage('Test') {
    sh 'sh ./test.sh'
  }
  stage('Push') {
    docker.withRegistry('https://registry.hub.docker.com','docker-hub-credentials') {
      app.push("${env.BUILD_NUMBER}")
      app.push("latest")
    }
  }
}
