pipeline{
    agent any

    stages{
        stage('Buils'){
            steps{
                sh 'ls -al'
            }
        }
        stage('Deploy'){
             steps{
                sshagent(credentials:['github_key1']){
                    sh '''
                        git config pull.rebase false
                        git checkout main
                        git pull
                        echo "Ths is for demo for Rowland" >> readme.md
                        git add readme.md
                        git commit -m "second commit"
                        git push git@github.com:azubuikeokom/test-jenkins.git main
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