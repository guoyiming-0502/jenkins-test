
pipeline {
    agent {                     // 声明使用的节点
        label 'master'
    }
    environment {               // 定义环境变量
        GIT_REPO = 'https://github.com/xx'
    }
    options {
        timestamps()
        timeout(time: 10, unit: 'MINUTES')
    }
    stages {
        stage('拉取代码') {      // 开始一个阶段
            environment {       // 定义该阶段的环境变量
                BRANCH = 'master'
            }
            steps {             // 该阶段需要执行一些步骤
                sh """
                    git clone $GIT_REPO
                    git checkout $BRANCH"
                """
            }
        }
        stage('构建镜像') {
            steps {
                sh '''
                    IMAGE=${image_hub}/${image_project}/${image_name}:${image_tag}
                    docker build . -t $IMAGE
                    docker push $IMAGE
                    docker image rm $IMAGE
                '''
            }
        }
    }
    post {
        always {            // 任务结束时总是执行以下操作
            deleteDir()     // 递归地删除当前目录。这里是作用于当前 agent 的 ${env.WORKSPACE} 目录
        }
    }
}
