@Library('jenkins-pipeline-shared-libraries') _

CREATE_RELEASE_BRANCHES = 'Jenkinsfile.create-release-branches'
CUSTOM_BASES=['optaplanner-quickstarts':'development','kogito-pipelines':'master']

pipeline {
    agent {
        label 'master'
    }
    stages {
        stage('Initialize') {
            steps {
                script {
                    def buildParams = []
                    addStringParam(buildParams, 'CUSTOM_BASE_NAME', getCustomBases())
                    echo "Pass ${CUSTOM_BASE_NAME}"
                    addStringParam(buildParams, 'REPOSITORIES', repositories.join(','))
                    buildJob(CREATE_RELEASE_BRANCHES, buildParams)
                }
            }
        }
    }
}

def buildJob(String jobName, List buildParams) {
   build(job: "./${jobName}", wait: true, parameters: buildParams, propagate: false)
}
void addStringParam(List params, String key, String value){
    params.add(string(name: key, value: value))
}


String getCustomBases(){
    return CUSTOM_BASES.toMapString()
}