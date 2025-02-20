pipeline{
    agent any
    stages {
        stage('Prepare Environment'){
            steps {
                script {
                    echo "Creating Virtual Environment"
                    bat 'python -m venv .venv'
                }
            }
        }
        stage('Activate the virtual environment'){
            steps{
                script{
                    echo "Activating Virtual Environment and Installing Dependencies"
                    bat '.venv\\Scripts\\activate'
                    bat 'pip3 install flask'
                }
            }
        }
        stage('Build the docker image'){
            steps{
                script{
                    echo "Building the docker image"
                    bat 'docker build -t devopscapsproject .'
                }
            }
        }
        stage('Run the docker image'){
            steps{
                echo "Running the docker image application"
                bat 'docker run -p 3000:3000 devopscapsproject'
            }
        }
        // stage('Delete the docker image'){
        //     steps{
        //         echo "Deleting the docker image"
        //         bat 'docker rmi -f devopscapsproject'
        //     }
        // }
    }
}