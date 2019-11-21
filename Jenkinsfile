pipeline {
    agent any
    environment{
        HOME = '.'
        AWS_ACCESS_KEY_ID='AKIA5ZB3TL4EQPA2CDH3'
        AWS_SECRET_ACCESS_KEY='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'
        AWS_DEFAULT_REGION='ap-southeast-1'
    }
    stages {
        stage('Build Stage') {
            steps {
                    sh("echo Build Stage!!");
                    sh("npm install");
            }
        }
        stage('Deploy Stage') {
            steps {
                sh("echo Deploy Step");
                sh("sam package --template-file template.yaml --output-template-file packaged.yaml --s3-bucket websockets-lambda-poc");
                sh("sam deploy --template-file packaged.yaml --stack-name simple-websocket-chat-app --capabilities CAPABILITY_IAM --parameter-overrides MyParameterSample=MySampleValue");
                sh("aws cloudformation describe-stacks --stack-name simple-websocket-chat-app --query 'Stacks[].Outputs'")
            }
        }
    }
}