pipeline {
    agent any

    stages {
        stage('Securitydeep FOSS') {
            steps {
                script {
                    //Prepare your credentials which will be used to access the SCM url given to scanner
                    //This is optional if your SCM url is public
                    def creds
                    withCredentials([usernamePassword(credentialsId: 'test-cred', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                      creds = "${USERNAME}:${PASSWORD}"
                    }
                    secdeep(
                        scmUrl: "https://github.com/mertakdut/Spring-Boot-Sample-Project", 
                        scm: "github", 
                        accessToken: creds,
                        applyThreshold: true,
                        threshold: [criticalThreshold: '0', highThreshold: '0', mediumThreshold: '0', lowThreshold: '0']
                    )
                }
            }
        }
    }
}
