node{
  stage('SCM Checkout'){
    git 'https://github.com/debolindhar/HelloWorldMaven'
  }
  stage('Compile Package'){
    sh 'mvn package'
  }
}
