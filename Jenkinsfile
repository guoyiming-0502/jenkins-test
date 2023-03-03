pipeline {
  agent any
  stages {
    stage('Test') {
      steps {
        echo "$A"   // 也可通过 $params.A 的格式读取构建参数，避免与环境变量重名
      }
    }

  }
  parameters {
    booleanParam(name: 'A', defaultValue: true, description: '')
    choice(name: 'E', choices: ['A', 'B', 'C'], description: '')
    string(name: 'B', defaultValue: 'Hello', description: '')
    text(name: 'C', defaultValue: '''Hello
World''', description: '')
    password(name: 'D', defaultValue: '123456', description: '')
    file(name: 'f1', description: '')
  }
}