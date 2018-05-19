node{
 
stage ('scm checkout'){   
checkout([$class: 'GitSCM',
    branches: [[name: '*/master']],
    doGenerateSubmoduleConfigurations: false,
    extensions: [],
    submoduleCfg: [],
    userRemoteConfigs: [[url: 'https://github.com/Shraddha-Chandrakar/master.git']]])
 }
 
 stage ('AppBuild'){
    sh 'mvn -f pom.xml clean package'
 }

stage ('deployment'){
    sh '''cp target/*.war /opt/apache-tomcat-8.5.31/webapps/
     sh /opt/apache-tomcat-8.5.31/bin/shutdown.sh
     sh /opt/apache-tomcat-8.5.31/bin/startup.sh'''
 }
 
 stage ('archive Articacts'){
    archiveArtifacts 'target/*.war'
  }
}
