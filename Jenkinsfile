node("docker") {
    docker.withRegistry('https://hub.docker.com', 'docker-hub-credential') {
    
        git url: "'https://github.com/manee2k6/jenkins-docker-slave.git'", credentialsId: 'github-manee2k6-credential'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "manee2k6/explore"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
