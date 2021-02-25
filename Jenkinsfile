node {

    def tomcatWeb='C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\webapps'
    def tomcatBin='C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\bin'
        stage('Git') {
                git "https://github.com/sindhurapadishala/dockerdemo.git"
        }
        stage('Maven Packaging'){
            //get maven home
            def mvnHome=tool name: 'maven system' ,type: 'maven'
            bat "mvn package"
        }
        stage('Deploy to tomcat'){
            bat "copy target\\docker_demo-0.0.1-SNAPSHOT.war \"${tomcatWeb}\\docker_demo-0.0.1-SNAPSHOT.war\""
        }
        stage('Start tomcat server'){
            sleep(time:5,unit:"SECONDS")
            bat """cd C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\bin
            startup"""
            sleep(time:100,unit:"SECONDS")
        }
}
