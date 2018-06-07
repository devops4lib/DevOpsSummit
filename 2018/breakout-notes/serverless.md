#Serverless Computing:

##Options
* Lambda
* Heroku
* Azure’s Lambda-like thing

A lot of us are interested but no experts. We’re not using it in production.

Concepts about Lamba
Called function
Small specific bit of code
Can we do something with it more than?
* Using Lambda for cron jobs?
 * It has a limit, hard coded of 5 minutes.
 * Limited scratch space, 400-500 MB.
Our sample small application ran in miliseconds, but you can build with a certa
Only get billed when someone uses it.
Very cheap, 2 dollars a month.
Can you make a call to Azure? Yes, but is

Heroku is another option which allows a wider language, but people think it seemed easier to run on a VPS or simply easier to use on a server.
Heroku’s using git itself to deploy, via git push, would have various events happen and that seemed very nice.

Why are we interested in serverless?
Using VPSes less, and people are limited to moving between VPS services and the ability to scale it out in a serverless environment would be good. The ability to simply scale with funding to pay for the events seems very nice.
The nice part of Lambda would be to combine it with something like a static site (S3, Jenkins) and then use Lambda to replicate many server functions.
The ability to push background jobs off of servers, or batch jobs.
The major issue we keep saying is scalability.

We covered all we know about this, we wish we had more experts and so we’re breaking to other groups.



