mvnHome = tool 'M3'

node {

    withMaven(maven:'maven') {


        stage('Build') {
            sh ''${mvnHome}/bin/mvn' clean install'

            def pom = readMavenPom file:'pom.xml'
            print pom.version
            env.version = pom.version
        }

        stage('Image') {
                sh "docker build -t piomin/account-service ."

        }

        stage ('Prod') {
                sh "kubectl apply -f deployment.yaml"      
        }
    

    }

}