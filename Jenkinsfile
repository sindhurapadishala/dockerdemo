node {

    def tomcatWeb='C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\webapps'
    def tomcatBin='C:\\Program Files\\Apache Software Foundation\\Tomcat 8.5\\bin'
        stage('Copy git file') {
                git "https://github.com/sindhurapadishala/dockerdemo.git"
        }
        stage('set java home'){
            //get maven home
            def mvnHome=tool name: 'maven system' ,type: 'maven'
            bat "set JAVA_HOME='C:\\Program Files\\Java\\jdk-11.0.2'"
        }
        stage('maven packaging'){
//          bat "setx PATH "%PATH%;%JAVA_HOME%\bin""
            bat "mvn package"
        }
        stage('Deploy to tomcat'){
            bat "copy target\\tommy_new.war \"${tomcatWeb}\\tommy_new.war\""
        }
        stage('start tomcat server'){
            sleep(time:5,unit:"SECONDS")
            bat "${tomcatBin}\\startup.bat"
            sleep(time:100,unit:"SECONDS")
        }
}
