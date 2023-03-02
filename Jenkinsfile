node{

                 stage('Clone repo'){
                 git branch: 'main', credentialsId: 'Githubcredentials', url: 'https://github.com/boddusri/SRE_TASK1.git'
                }

                stage('Maven Build'){
                def mavenHome = tool name: "Maven-3.9.0", type: "maven"
                def mavenCMD = "${mavenHome}/bin/mvn"
                sh "${mavenCMD} clean package"
                }
                stage('upload war to nexus'){
                        nexusArtifactUploader artifacts: [
                        [
                                artifactId: 'sriproj',
                                classifier: '',
                                file: 'target/sriproj-3.0.0.war',
                                type: 'war'
                                ]
                        ],
                                credentialsId: 'nexus3',
                                groupId: 'in.sri',
                                nexusUrl: 'http://43.207.78.204:8081/repository/Sidgsrelease/',
                                nexusVersion: 'nexus3',
                                repository: 'Sidgsrelease/',
                                protocol: 'http',
                                version: '3.0.0'
                        }
        }
