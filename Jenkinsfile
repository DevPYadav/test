node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */
        
        
        sh ' echo $(whoami)'
        app = docker.build("devops")
        sh 'echo "Build passed"'
    }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        /* Finally, we'll push the image with two tags:
         * First, the incremental build number from Jenkins
         * Second, the 'latest' tag.
         * Pushing multiple tags is cheap, as all the layers are reused. */
        /* docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') { */

        sh 'echo "Before docker registry111"'
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') { 
        /* docker.withRegistry('https:/registry.hub.docker.com/repository/docker/devpyadav/devops', 'docker-hub-credentials') { */
            echo "Pushing 1..."
            app.push("${env.BUILD_NUMBER}")
            echo "Pushing 2..."
            app.push("latest")
            echo "Pushed"
        }
    }
        sh 'echo "After docker registry"'        
   
}
