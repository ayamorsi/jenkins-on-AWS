pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                 sh 'echo "Hello World"'
                 sh '''
                     echo "Multiline shell steps works too"
                     ls -lah
                 '''
             }
         }
         stage('Lint HTML') {
              steps {
                  sh 'tidy -q -e *.html'
              }
         }
          stage('Upload to AWS') {
        steps {
          withAWS(region:'us-east-1',credentials:'0b9ba270-5642-4215-8612-344ba68effa0') {
            s3Upload(pathStyleAccessEnabled:true, payloadSigningEnabled: true, file:'index.html', bucket:'c3pipeliness')
          }
         }
     }
}
     }
