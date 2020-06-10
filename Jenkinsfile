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
    //Create Package ID
    def timeStamp = Calendar.getInstance().getTime().format('YYYYMMdd-hhmmss',TimeZone.getTimeZone('CST'))
    bat "echo ${timeStamp}"
    def day = timeStamp.substring(0,8)
    bat "echo ${day}"
    
    bat "echo ${currentBuild.number}"
    
    def packageid = "${day}.${currentBuild.number}"
    bat "echo ${packageid}"
    
    //Publish package to Nexus Server
    nexusPublisher nexusInstanceId: 'JavaRelease', nexusRepositoryId: 'maven-releases', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: '\\target\\jb-hello-world-maven-0.1.0.jar']], mavenCoordinate: [artifactId: 'jb-hello-world-maven', groupId: 'org.springframework', packaging: 'jar', version: '${packageid}']]]
  }
}
