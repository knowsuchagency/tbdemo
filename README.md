# tablib, flask, and openshift!
## Check out the web-app [here!](http://tbdemo-bamf.rhcloud.com)

```python
from flask import Flask, render_template, request
import tablib


app = Flask(__name__)
app.config.from_pyfile('flaskapp.cfg')


@app.route('/')
def index():
    return render_template('index.html')


@app.route('/upload', methods=['POST'])
def upload():
    table = tablib.Dataset()
    file = request.files['file']
    table.csv = file.read()
    return table.html


if __name__ == '__main__':
    app.run()
```
'''
