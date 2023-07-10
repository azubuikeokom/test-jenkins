pipeline{
    agent none

    stages{
        stage('Buils'){
            steps{
                sh 'ls -al'
            }
        }
        stage('Deploy'){
             steps{
                sshagent(credentials:['github_key']){
                    sh '''
                        echo "Pushed from jenkins server" >> readme.md
                        git add readme.md
                        git commit -m "second commit"
                        git push git@github.com:azubuikeokom/test-jenkins.git
                    '''
                }
             }
             post{
                success{
                    echo "Deploy was successful"
                }
                failure{
                    echo "Deploy failed"
                }
             }
        }
    }
}