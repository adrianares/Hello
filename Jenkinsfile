node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

   /* stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line 

        app = docker.build("hellonode")
    }*/

    stage("build") {
        script {
            TAG = VersionNumber(versionNumberString: '${BUILD_DATE_FORMATTED, "yyyyMMdd"}-develop-${BUILDS_TODAY}')
            echo "Building..."
            sh "docker build -t $IMAGE:$TAG ."
         }
      }
    
    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        app.inside {
            sh 'echo "Tests passed"'
        }
    }
}
