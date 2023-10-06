pipeline{
    agent any
    tools{
        
        maven 'maven3'
    }
    stages{
        stage("checkout"){
            steps{
                sh "ls"
                git branch:"main", url:"https://github.com/bhattur/course3-jenkins-gs-spring-petclinic"
                sh "ls"
            }
        }
        stage("build"){
            steps{
                sh "mvn package"
            }
        }
        stage("capture"){
            steps{
                archiveArtifacts artifacts: '**/target/*.jar', followSymlinks: false
                jacoco()
                junit '**/target/surefire-reports/TEST*.xml'
                emailext body: '', recipientProviders: [developers()], subject: 'developers', to: 'rav@gmail.com'
            }
        
        }
    }
}