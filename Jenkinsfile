node {

    checkout scm
    mvnHome = tool 'M3'


    env.DOCKER_API_VERSION="1.23"
    
    sh "git rev-parse --short HEAD > commit-id"

    stage "Build"
    
        sh "'${mvnHome}/bin/mvn' clean install"
        sh "docker build -t piomin/account-service ."


    stage "Deploy"

        sh " kubectl apply -f deployment-account.yml"
        sh "kubectl rollout status deployment/account-service"

}
