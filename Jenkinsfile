pipeline {
    agent any 
    parameters {
        //string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod')
        choice(name: 'VERSION', choices: ['1.1.0','1.1.1','1.1.2'] description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    stages {
        stage("Build") {
            steps {
                echo 'building the application ....................'
            }
        }
        stage("Test") {
            when {
                expression {
                    params.executeTests == true
                }
            }
            steps {
                echo 'testing the application ...................'
            }
        }
        stage("Deploy") {
            steps {
                echo 'deploying the application ...................'
                echo "the deploying version is ${params.VERSION}"
            }
        }
    }
}
