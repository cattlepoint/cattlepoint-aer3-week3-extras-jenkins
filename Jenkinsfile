/* Requires the Docker Pipeline plugin */
pipeline {
    agent {
        docker {
            image 'python:3.13.4-alpine3.22'
            args  '-u root --entrypoint ""'
        }
    }

    stages {
        stage('Environment Info') {
            steps {
                echo '👋 Checking versions...'
                sh 'python --version'
                sh 'cat /etc/alpine-release'
            }
        }

        stage('Hello World Setup') {
            steps {
                echo '📄 Creating hello_world.py'
                sh '''
                    cat > hello_world.py <<'EOF'
print("Hello, World! 🚀")
EOF
                '''
            }
        }

        stage('Run Hello World') {
            steps {
                echo '▶️ Executing hello_world.py'
                sh 'python hello_world.py'
            }
        }
    }

    post {
        always {
            echo '🏁 Pipeline complete.'
        }
    }
}
