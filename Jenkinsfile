node("docker") {
    docker.withRegistry('aya', 'aya2') {
    
        git url: "https://github.com/ayasalahbakr/Devops", credentialsId: 'ayasalahbakr'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "your-project-name"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
