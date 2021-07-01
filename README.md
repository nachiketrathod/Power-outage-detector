# Power-outage-detector

<p align="center">
<figure>
    <img src="https://i.ibb.co/3f7JSRm/urbansolar.gif" alt="urbansolar" style="border:0px solid purple">
</figure>
</p>

<p align="left"> 
      <a href="https://www.twitter.com/4ccess0denie1">
           <img alt="Twitter Follow" src="https://img.shields.io/twitter/follow/4ccess0denie1?color=%2300acee&label=Follow%20%404ccess0denie1&logo=Twitter&logoColor=%2300acee&style=flat-square"></a>
           <img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/nachiketrathod/HTTP.Request.Smuggling.Lab?logo=github&style=flat-square">
	   <img alt="GitHub repo size" src="https://img.shields.io/github/repo-size/nachiketrathod/HTTP.Request.Smuggling.Lab?logo=Github&style=flat-square">
</p><hr>

# How it works?

* The script basically divided into 2 parts `Client-side` and `server-side`.
* The script on the server-side will Ping to the clinet-side script after minutes of time interval(e.g 3 or 5 mins)
* If the server get the response from the client-side then everything is fine else either there is a power-outage or internt connection is down.
* In the down period of time server will send an sms to your configured application like email or other notification apps (here I've used pushbullets)

# Pre-requisites:

* [`raspberrypi`](https://www.raspberrypi.org/) for your client-side script.
* [`server`](https://www.cloudatcost.com/) for serve-side script I've used my cloudatcost server.<hr>
