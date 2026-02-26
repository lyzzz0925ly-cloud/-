# -
没问题
from flask import Flask, request

app = Flask(__name__)

# 主页：带选项按钮
@app.route('/')
def index():
    return '''
    <h1>我的互动小网站</h1>
    <p>点一个选项试试：</p>
    <a href="/choice?opt=1"><button>选项1：你好</button></a>
    <a href="/choice?opt=2"><button>选项2：今天开心吗</button></a>
    <a href="/choice?opt=3"><button>选项3：来点鼓励</button></a>
    '''

# 处理选择
@app.route('/choice')
def choice():
    opt = request.args.get('opt')
    if opt == '1':
        msg = "你好呀！欢迎来到我的小站～"
    elif opt == '2':
        msg = "当然开心！因为你在访问我呀"
    elif opt == '3':
        msg = "你超棒的！继续加油！"
    else:
        msg = "请点上面的按钮哦"

    return f'''
    <h2>{msg}</h2>
    <br>
    <a href="/"><button>返回</button></a>
    '''

if __name__ == '__main__':
    app.run(debug=True)
