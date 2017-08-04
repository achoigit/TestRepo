node {
  stage('Checkout') {
    checkout scm    
  }
  stage('Build') {
    app = docker.build("testrepo/hellonode")
  }
}
