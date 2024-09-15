pipeline {
    agent any
    tools {
        maven "maven-3.6"
    }
    stages {
        stage("build jar") {
            steps {
                script {
                    echo "building the application ..................."
                    sh "mvn package"  
                }
            }

        }
        stage("build image") {
            steps {
                script {
                    echo "building the docker image .................."
                    withCredentials([usernamePassword(credentialsId: "docker-user", passwordVariable: "PASSWORD", usernameVariable: "USERNAME")]) {
                        sh "docker build -t dockertvk/nana-java-maven-app:2.0 ."
                        sh "echo $PASSWORD | docker login -u $USERNAME --password-stdin"
                        sh "docker push dockertvk/nana-java-maven-app:2.0"
                    }
                }
            }
        }
        stage("deploy") {
            steps {
                script { 
                    echo "deploying the application ............................"
                }
            }
        }
    }
}
