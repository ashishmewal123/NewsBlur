pipeline {
    agent any

    parameters {
        choice(name: 'COMPONENT', choices: ['app', 'monitor', 'node', 'redis', 'task'], description: 'Choose the component to build')
    }

    environment {
        DOCKER_COMPOSE_FILE = 'docker-compose.yml'
        // Uncomment and replace with your Docker credentials ID if needed
        // DOCKER_CREDENTIALS_ID = 'your-docker-credentials-id'
    }

    stages {
        stage('Checkout') {
            steps {
                // Only for demonstration, assuming your repository is already cloned
                echo 'Checking out the repository...'
                 git 'https://github.com/ashishmewal123/NewsBlur.git'
            }
        }

        stage('Build') {
            steps {
                script {
                    if (params.COMPONENT == 'app') {
                        echo "Building app component"
                        sh "docker-compose -f ${DOCKER_COMPOSE_FILE} build newsblur"
                    } else if (params.COMPONENT == 'monitor') {
                        echo "Building monitor component"
                        sh "docker-compose -f ${DOCKER_COMPOSE_FILE} build monitor"
                    } else if (params.COMPONENT == 'node') {
                        echo "Building node component"
                        sh "docker-compose -f ${DOCKER_COMPOSE_FILE} build node"
                    } else if (params.COMPONENT == 'redis') {
                        echo "Building redis component"
                        sh "docker-compose -f ${DOCKER_COMPOSE_FILE} build redis"
                    } else if (params.COMPONENT == 'task') {
                        echo "Building task component"
                        sh "docker-compose -f ${DOCKER_COMPOSE_FILE} build task"
                    } else {
                        echo "Invalid component: ${params.COMPONENT}"
                    }
                }
            }
        }
    }
}
