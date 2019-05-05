def MVN_COMMAND = """mvn test -Dtest-parameter="TBD" -Dtest=PrintParamTests"""

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
                    steps {
                        build job: 'Experimental_Parameterized_Job',
                                parameters: [
                                        string(name: 'MVN_STRING', 
                                                value: MVN_COMMAND.replaceFirst("TBD", "First Build"))
                                ]
                    }
                }
                stage('Second Build') {
                    steps {
                        build job: 'Experimental_Parameterized_Job',
                                parameters: [
                                        string(name: 'MVN_STRING', 
                                                value: MVN_COMMAND.replaceFirst("TBD", "Second Build"))
                                ]
                    }
                }
                stage('Third Build') {
                    steps {
                        build job: 'Experimental_Parameterized_Job',
                                parameters: [
                                        string(name: 'MVN_STRING', 
                                                value: MVN_COMMAND.replaceFirst("TBD", "Third Build"))
                                ]
                    }
                }
            }
        }
    }
}
