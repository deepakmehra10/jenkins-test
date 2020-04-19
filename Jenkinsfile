pipeline {
    agent any
    stages {
        stage('build') {
         when{
            branch 'master'
          }
            steps {
            script {
                      withCredentials([
                        usernamePassword(credentialsId: 'apigee-credentials',
                          usernameVariable: 'username',
                          passwordVariable: 'password')
                      ]) {
                        print 'username=' + username + 'password=' + password
                        print 'username.collect { it }=' + username.collect { it }
                                    print 'password.collect { it }=' + password.collect { it }
                 environment = "test"
                 sh "echo 'Hello testing...'"
                 sh "unset JAVA_HOME && mvn clean spring-boot:run"
                 sh "curl -XGET 127.0.0.1:9000/welcome"
                      }
                    }
            }
        }
    }
}
