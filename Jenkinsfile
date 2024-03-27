node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
       app = docker.build("danieldann/kiii_jenkins")
    }
    stage('Push image') {   
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${env.master}-${env.1}")
            app.push("${env.master}-latest")
            // signal the orchestrator that there is a new version
        }
    }
}