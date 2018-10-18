pipeline {
    agent any

    parameters {
        string(name: 'REGION', defaultValue: 'us-west-2', description: 'AWS region')
        string(name: 'PROJECT_NAME', defaultValue: '', description: 'CodeBuild project name')
    }

    stages {
        stage('CodeBuild') {
            steps {
                script {
                    awsCodeBuild(
                        projectName: params.PROJECT_NAME,
                        region: params.AWS_REGION,
                        credentialsType: 'keys',
                        sourceControlType: 'jenkins',
                        sourceVersion: env.GIT_COMMIT,
                    )
                }
            }
        }
    }
}
