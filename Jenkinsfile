node{
  stage('SCM Checkout'){
    git 'https://github.com/debolindhar/HelloWorldMaven'
  }
  stage('Compile Package'){
    //Get Maven Home path
    def mvnHome = tool name: 'JenkinsMaven', type: 'maven'
    bat "${mvnHome}/bin/mvn package"
  }
  stage('Publish to Nexus'){
    //Get current Build number
    echo "current build number: ${currentBuild.number}"
    echo "current date: ${LocalDate.now()}"
    //Publish package to Nexus Server
    nexusPublisher nexusInstanceId: 'JavaRelease', nexusRepositoryId: 'maven-releases', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: '\\target\\jb-hello-world-maven-0.1.0.jar']], mavenCoordinate: [artifactId: 'jb-hello-world-maven', groupId: 'org.springframework', packaging: 'jar', version: '0.3.0']]]
  }
}
