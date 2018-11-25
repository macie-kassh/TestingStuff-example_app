node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

      /*  app = docker.build("getintodevops/example-app") */
        app = docker.build("macie-kassh/example_app") 

    }

    stage('Push image') {
        /* Finally, we'll push the image into Docker Hub */
        /* these credentials are the ones which enter in jenkines credentials 
           there are two arguments 
           first is the registery of the docker. 
           second is the ID in the jenkins configuration file
        */
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("latest") /* push the docker to the registery */
        }
    }
}
