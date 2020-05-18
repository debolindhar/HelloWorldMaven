node{
  stage('SCM Checkout'){
    git 'https://github.com/debolindhar/HelloWorldMaven'
  }
  stage('Compile Package'){
    //Get Maven Home path
    def mvnHome = tool name: 'JenkinsMaven', type: 'maven'
    sh "${mvnHome}/bin/mvn package"
  }
}
