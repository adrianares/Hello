node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */
        
        TAG = VersionNumber(versionNumberString: '${BUILD_DATE_FORMATTED, "yyyyMMdd"}-v-${BUILDS_TODAY}')
                            //${YEARS_SINCE_PROJECT_START,x}-${MONTHS_SINCE_PROJECT_START,xx}-${BUILD_MONTH}')
            echo "Building..."

        app = docker.build("hellonode_" + TAG)
    }
    
    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        app.inside {
            sh 'echo "Tests passed"'
        }
    }
}
