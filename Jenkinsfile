pipeline {
    agent any
    stages {
       stage('Lint HTML') {
             steps {
                 tidy -q -e *.html
             }
       }
       stage('Upload to AWS') {
             steps {
                 withAWS(region:'us-west-2',credentials:'S3Access') {
                 sh 'echo "Uploading content with AWS creds"'
                     s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'ci-cd-static-jenkins-pipeline')
                 }
             }
        }
    }
}
