# Tablib, Flask, and Openshift!
## Check out the web-app [here!](http://tbdemo-bamf.rhcloud.com)

### [__Source Code__](https://github.com/knowsuchagency/tbdemo) <- Forked from Ryan Jarvinen's [flask-base](https://github.com/ryanj/flask-base)
### [Flask](http://flask.pocoo.org/docs/0.10/)
### [Tablib](http://docs.python-tablib.org/en/latest/)
### [Openshift](http://www.openshift.org/)

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
