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
                 sh "cd ./apigee/Billing && mvn clean install -P${environment} -Dusername=${username} -Dpassword=${password} -Doptions=override"
                      }
                    }
            }
        }
    }
}
