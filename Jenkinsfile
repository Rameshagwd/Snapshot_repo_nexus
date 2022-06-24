pipeline {
    agenty any
    stages: {
        stage: ('Git Clone') {
            steps: {
                git branch: 'main', url: 'https://github.com/Rameshagwd/Snapshot_repo_nexus.git'         
            }
        }

        stage: ('MVN Clean') {
            steps: {
                sh 'mvn clean'
            }
        }

        stage: ('MVN compile') {
            steps: {
                sh 'mvn compile'
            }
        }

        stage: ('MVN test') {
            steps: {
                sh 'mvn test'
            }
        }

        stage: ('MVN package') {
            steps: {
                sh 'mvn package'
            }
        }
        stage: ('Deploy .jar/war artifact to Nexus') {
            steps: {
                script {
                    pom = readMavenPom file: 'pom.xml'
                    nexusArtifactUploader artifacts [
                        [
                            artifactId: 'Snapshot_repo_nexus',
                            classifier: '',
                            file: 'target/Snapshot_repo_nexus-${pom.version}.jar',
                            type: 'jar'
                            
                        ]
                        
                    ],

                    credentialsId: 'Nexus',
                    groupId: 'com.javatpoint.application1',
                    nexusVersion: 'nexus3',
                    nexusUrl: '10.32.39.203:8081',
                    protocol: 'http',
                    repository: 'Snapshot_repo_nexus',
                    version: "${pom.version}"
                }
                
            }
        }
    }
}