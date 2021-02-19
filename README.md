'''
项目越多，越有可能在不同版本的 Python，或者至少在不同 Python 库的版本上工作。
virtualenv 能够允许多个不同版本的 Python 安装，每一个服务于各自的项目。
它实际上并没有安装独立的 Python 副本，只是提供了一种方式使得环境保持独立。
'''

# 安装 virtualenv 库：
$ pip3 install virtualenv

'''
# 升级 pip 和 virtualenv 到最新版：
$ pip3 install -U pip virtualenv

# 查看 virtualenv 的版本：
$ pip3 freeze | grep virtualenv
'''

# 创建虚拟环境：
$ virtualenv -p python3 venv

# 启动虚拟环境或进入虚拟环境：
$ source ~/venv/bin/activate #.\venv\Scripts\activate

# 虚拟环境中安装 Flask 框架 1.0.2 版本：
$ pip install flask==1.0.2

# 项目目录结构：
'''
• flaskr：项目总目录。其中会存放数据库代码文件 schema.sql 和 主代码文件 flaskr.py。
• static：项目的静态资源目录。用于存放 css 和 javascript 文件。
• templates：项目前端模板文件的目录。用于存放前端页面模板。
'''

# flaskr 目录下新建 schema.sql ：
'''
DROP TABLE IF EXISTS entries;

CREATE TABLE entries (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    title STRING NOT NULL,
    text STRING NOT NULL
);
'''

# Python3 命令行交互解释器创建数据库，
# 导入并调用主代码文件flaskr.py的数据库初始化函数：
'''
>>> from flaskr import init_db
>>> init_db()
'''

# virtualenv下启动应用：
(venv) ~\flaskr> python .\flaskr.py
'''
 * Serving Flask app "flaskr" (lazy loading)
 * Environment: development
 * Debug mode: on
 * Restarting with stat    
 * Debugger is active!
 * Debugger PIN: 150-362-392
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
'''

# 启动应用：
$ export FLASK_ENV=development #设置FLASK_ENV环境变量为development
$ export FLASK_DEBUG=1 FLASK_APP=flaskr.py #开启调试模式启动
$ flask run -h 0.0.0.0 -p 8080 #python3 -m flask run
'''
 * Serving Flask app "flaskr.py" (lazy loading)
 * Environment: development
 * Debug mode: on
 * Running on http://0.0.0.0:8080/ (Press CTRL+C to quit)
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 214-530-745
172.16.2.250 - - [21/Apr/2020 10:22:23] "GET / HTTP/1.1" 200 -
172.16.2.250 - - [21/Apr/2020 10:22:24] "GET /static/style.css HTTP/1.1" 200 -
'''
