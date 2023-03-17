# flask


## flask简单的上传下载实现

```python
from flask import Flask,render_template,request,send_file
from werkzeug.utils import secure_filename
#创建app
app = Flask(__name__)
#上传文件-网页端
html_code = '<!DOCTYPE html>' \
            '<html lang="en">' \
            '<head><meta charset="UTF-8"><title>Title</title></head>' \
            '<body><form action="/" enctype="multipart/form-data" method="post">' \
            '<input type="file" name="file">' \
            '<input type="submit" value="上传"></form>' \
            '</body></html>'

#上传文件
@app.route('/',methods=['POST','GET'])
def upload_file():
    #请求为POST
    if request.method =='POST':
        #html中 读取input标签 name = ”file“ 中的文件
        f = request.files['file']   #中括号！！
        #secure_filename
        filename = secure_filename(f.filename)
        f.save(filename)
        return "successfully"
    else:return html_code
#下载文件
@app.route('/<filename>')  #输入文件名
def download_file(filename):
    #返回  参数：as_attachment  是否可下载
    #浏览器输入：http://127.0.0.1:5000/文件名.后缀  
    # 即可下载
    return send_file(filename,as_attachment=True)  
#运行
if __name__ == '__main__':
    app.run()
```

‍

