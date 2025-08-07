pipeline {
    agent docker-swarm-manager
    environment {
        STACK_NAME = 'socialecho'
    }
    stages {
        stage('Deploy Stack') {
            steps {
                sh "docker stack deploy -c docker-stack.yaml $STACK_NAME"
            }
        }
    }
}
