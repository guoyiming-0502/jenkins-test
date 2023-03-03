pipeline {
    agent any
    parameters {
        booleanParam(name: 'A', defaultValue: true, description: '')   // 布尔参数
        choice(name: 'E', choices: ['A', 'B', 'C'], description: '')   // 单选参数，输入时会显示成下拉框
        string(name: 'B', defaultValue: 'Hello', description: '')      // 字符串参数，在 Web 页面上输入时不能换行
        text(name: 'C', defaultValue: 'Hello\nWorld', description: '') // 文本参数，输入时可以换行
        password(name: 'D', defaultValue: '123456', description: '')   // 密文参数，输入时会显示成密文
        file(name: 'f1', description: '')                              // 文件参数，输入时会显示文件上传按钮
    }
    stages {
        stage('Test') {
            steps {
                echo "$A"   // 也可通过 $params.A 的格式读取构建参数，避免与环境变量重名
            }
        }
    }
}
