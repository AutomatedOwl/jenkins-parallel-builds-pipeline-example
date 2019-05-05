pipeline {
    agent {
        kubernetes {
            label "automation-tests-slave"
            containerTemplate {
                name "k8s-slave-jdk12-alpine"
                image "openjdk:12-jdk-alpine"
                ttyEnabled true
                command 'cat'
            }
        }
    }
    stages {
        stage('Run Tests') {
            parallel {
                stage('First Build') {
                    build job: 'Experimental_Parameterized_Job',
                            parameters: [
                                    string(name: 'MVN_STRING', value: """mvn test -Dtest-parameter="First Build" -Dtest=PrintParamTests""")
                            ]
                }
                stage('Second Build') {
                    build job: 'Experimental_Parameterized_Job',
                            parameters: [
                                    string(name: 'MVN_STRING', value: """mvn test -Dtest-parameter="Second Build" -Dtest=PrintParamTests""")
                            ]
                }
                stage('Third Build') {
                    build job: 'Experimental_Parameterized_Job',
                            parameters: [
                                    string(name: 'MVN_STRING', value: """mvn test -Dtest-parameter="Third Build" -Dtest=PrintParamTests""")
                            ]
                }
            }
        }
    }
}
