@Library(['github.com/indigo-dc/jenkins-pipeline-library@stable/2.1.0']) _

def projectConfig

pipeline {
    agent any

    stages {
        stage('SQA baseline criterion: QC.FAIR') {
            steps {
                script {
                    projectConfig = pipelineConfig(
                        configFile: '.sqa/config.yml',
                        scmConfigs: [ localBranch: true ],
                        validatorDockerImage: 'eoscsynergy/jpl-validator:1.2.0'
                    )
                    buildStages(projectConfig)
                }
            }
            post {
                cleanup {
                    cleanWs()
                }
            }
        }
    }
}