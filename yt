from flask import Flask, render_template, request, redirect, url_for, flash
from pytube import YouTube
import os

app = Flask(__name__)
app.secret_key = 'asd'  # Change this to a random secret key for session management

@app.route('/')
def index():
    return render_template('downloader.html')

@app.route('/download', methods=['POST'])
def download():
    url = request.form['url']
    try:
        yt = YouTube(url)
        stream = yt.streams.get_highest_resolution()
        stream.download()  # You can specify a path here if needed
        flash('Download completed successfully!')
    except Exception as e:
        flash(f'An error occurred: {e}')
    
    return redirect(url_for('index'))

if __name__ == '__main__':
    app.run(debug=True)
