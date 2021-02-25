node {

    def tomcatWeb='C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\webapps'
    def tomcatBin='C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\bin'
        stage('Copy git file') {
                git "https://github.com/sindhurapadishala/dockerdemo.git"
        }
        stage('maven package'){
            //get maven home
            def mvnHome=tool name: 'maven system' ,type: 'maven'
            bat "mvn package"
        }
        stage('Deploy to tomcat'){
            bat "copy target\\docker_demo-0.0.1-SNAPSHOT.war \"${tomcatWeb}\\docker_demo-0.0.1-SNAPSHOT.war\""
        }
        stage('start tomcat server'){
            sleep(time:5,unit:"SECONDS")
            bat """C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\bin\\startup.bat"""
            sleep(time:100,unit:"SECONDS")
        }
}
