properties([pipelineTriggers([githubPush()])])
node('linux') {
    git url: 'https://github.com/TonyBlonigan/infrastructure-pipeline.git', branch: 'master'
    stage('Test') {
        sh "env"
    }
    stage ("GetInstances") {
        sh "aws ec2 describe-instances --region us-east-1"
    }
    stage ("CreateInstance") {
        aws ec2 run-instances \
        --image-id ami-013be31976ca2c322 \
        --count 1 \
        --instance-type t2.micro \
        --key-name in_class_2 \
        --security-group-ids sg-0c5523b267fdfc1a9 \
        --subnet-id subnet-09d3b89d760a3125f \
        --region us-east-1
    }
}
