# lab
lab


node {
    def mvnHome
    stage('Pull from scm') {
        git 'https://github.com/babaeli/time-tracker.git'
    }
    stage('Build artifact') {
        // Run the maven build
        mvnHome = tool (name: '3.6', type: 'maven')
        sh "'${mvnHome}/bin/mvn' clean package"
    }
    stage('Deploy artifact') {
        sh "cp /var/lib/jenkins/workspace/class-work/web/target/*.war /usr/share/tomcat/webapps/"

    }
    //stage('Results') {
      //  junit '**/target/surefire-reports/TEST-*.xml'
        //archive 'target/*.jar'
    }
