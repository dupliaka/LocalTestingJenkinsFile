@Library('jenkins-pipeline-shared-libraries') _

pipeline {
    agent {
        label 'master'
    }

    parameters {
        string(name: 'BUILD_NAME', defaultValue: 'FirstBuild', description: 'Branch name will be')
    }
    environment {
        BASE_BRANCH = 'master'
    }

    stages {
        stage('Initialize') {
            steps {
                script {
                    echo 'Initialize'
                    currentBuild.displayName = "${getBuildName()}"
                }
            }
        }
    }
}

String getBuildName() {
    return params.BUILD_NAME
}