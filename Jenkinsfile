def COLOR_MAP = [
    'SUCCESS': 'good', 
    'FAILURE': 'danger',
]


pipeline{
    agent any
    tools{
        maven 'maven3'
    }
    stages{
        stage('Git Checkout'){
            steps{
                git 'https://github.com/bhuvanbudaviwork/my-prime-v2.git'
            }
        }
         stage('Sonarqube Scanning'){
             environment{
                 sonarhome=tool 'sonarqube-tool';
             }
            steps{
                sleep time: 5, unit: 'MINUTES'
                withSonarQubeEnv('sonarqube-system'){
                    sh """
                    ${sonarhome}/bin/sonar-scanner \
                    -Dsonar.projectName=staging-project \
                    -Dsonar.projectKey=stagingkey \
                    -Dsonar.projectVersion=1.0 \
                    -Dsonar.sources=src \
                    -Dsonar.java.binaries=target 
                    """
                    
                    
                }
            }
        }
        stage('Quality Gate Check'){
            steps{
                sleep time: 2, unit: 'MINUTES'
                timeout(time:1, unit:'HOURS'){
                    waitForQualityGate abortPipeline:true
                }
            }

        }
         stage('Trivy FileSystem Scan'){
            steps{
                sleep time: 3, unit: 'MINUTES'
                sh 'trivy fs . > trivy-scan-report'
            }
        }
         stage('Maven Clean'){
            steps{
                sh 'mvn clean'
            }
        }
        stage('Maven Package'){
            steps{
                sleep time: 3, unit: 'MINUTES'
                sh 'mvn package -DskipTests'
            }
        }
        stage('OWASP File System scan'){
            steps{
                dependencyCheck ( 
                    additionalArguments:'--scan target/ --format XML',
                odcInstallation:'dependency-check')
                dependencyCheckPublisher(
                    pattern:'**/dependency-check-report.xml',
                failedTotalHigh:10,
                failedTotalCritical:10)
            }
        }
         stage('Publish Artifact to nexus'){
            steps{
                sleep time: 4, unit: 'MINUTES'
                nexusArtifactUploader(
                    nexusVersion:'nexus3',
                    protocol:'http',
                    nexusUrl:'16.16.169.217:8081',
                    groupId:'staging',
                    version:"${BUILD_ID}-${BUILD_TIMESTAMP}",
                    repository: 'staging-repo',
                    credentialsId: 'nexus-creds',
                    artifacts:[
                        [
                            artifactId: 'vproapp', 
                            classifier: '', 
                            file: 'target/amazon-prime-clone.war', 
                            type: 'war'
                        ]
                    ]
                )
                
            }
        }
        
         
         stage('Deploy to Containerr'){
            steps{
                sleep time: 2, unit: 'MINUTES'
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat-creds', path: '', url: 'http://16.16.79.128:8081')], contextPath: null, war: '**/*.war'
            }
        }
        
        
        
    }
    
   post {
        always {
            echo 'Slack Notifications.'
            slackSend channel: '#all-staging-environment',
                color: COLOR_MAP[currentBuild.currentResult],
                message: "*${currentBuild.currentResult}:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER} \n More info at: ${env.BUILD_URL}"
        }
    }

    
}
