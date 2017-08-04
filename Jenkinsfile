node {
  stage('Checkout') {
    checkout scm    
  }
  stage('Build') {
    app = docker.build("testrepo/hellonode")
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
