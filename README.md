from flask import Flask, render_template, request, redirect

app = Flask(__name__)

stamps = []

@app.route('/')
def index():
    return render_template('index.html', stamps=stamps)

@app.route('/add_stamp', methods=['POST'])
def add_stamp():
    stamp_name = request.form.get('stamp_name')
    stamps.append(stamp_name)
    return redirect('/')

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=3000)

