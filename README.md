# QTK
test QTK
from flask import Flask, render_template
import pyodbc

app = Flask(__name__)

@app.route('/')
def index():
    conn_str = (
        r'DRIVER={Microsoft Access Driver (*.mdb, *.accdb)};'
        r'DBQ=F:\\Desktop\\z\\compelete_Parsian.accdb;'
    )
    conn = pyodbc.connect(conn_str)
    cursor = conn.cursor()
    cursor.execute('SELECT * FROM [QTK]')
    data = cursor.fetchall()
    return render_template('index.html', data=data)

if __name__ == '__main__':
    app.run()
