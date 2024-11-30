@Library("Shared") _
pipeline{
    agent { label "star" }
    
    stages{
        stage("Code"){
           steps{
               script{
                   code_clone("https://github.com/himanshi1107/django-notes-app.git", "dev")
               }
           } 
        }
        stage("Build"){
           steps{
               script{
                   docker_build("notes-app","latest","himanshi1107")
               }
           } 
        }
        stage("Push to DockerHub"){
           steps{
              script{
                  dockerhub_push("notes-app","latest","himanshi1107")
              }
           } 
        }
        stage("Deploy"){
           steps{
               script{
                docker_compose()
               }
           } 
        }
    }
}
