from flask import Flask, session, redirect
from pushbullet import PushBullet
from threading import Timer
from time import sleep
from datetime import timedelta
from datetime import datetime

app = Flask(__name__)
app.secret_key = "G&*G^g9#78h7*btu6gy9HBvy613S`342!3%fd 65F$5D465&f7"
apiKey = "________________________________" #your apikey of pushbullet
p = PushBullet(apiKey)


@app.before_request
def make_session_permanent():
    session.permanent = True
    app.permanent_session_lifetime = timedelta(minutes=3)


def do_something_1(test):
    global p
    with app.test_request_context():
        if "connected" not in session:
            print("Server is Down, \nSending Message")
            p.push_note('Server is Down', 'Unable to connect with server\n'+ datetime.now().strftime("%d/%m/%Y %H:%M:%S"))
        else:
            print("server is up")


def newTimer():
    global t
    t = Timer(180, do_something_1, args=("test",))
    print("Timer started.....")


newTimer()


@app.route('/', methods=['GET'])
def respond():
    session['response'] = 'session#1'
    return "Home"


@app.route('/get')
def getVariable():
    session['connected'] = "connected"
    newTimer()
    return "Session set successfully"


@app.route('/ping', methods=['GET'])
def post_something():
    if "connected" not in session:
        print("redirecting")
        return redirect("/get", code=302)
    global t
    t.cancel()
    newTimer()
    t.start()
    print("\nReset Timer Successfully!!!")
    return "Connected"


@app.route('/connect')
def index():
    p.push_note('Server Testing', 'This is test message')
    return "notification sent"


if __name__ == '__main__':
    app.debug = False
    app.run(threaded=True, port=5000, host="0.0.0.0")
