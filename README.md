# dash_heroku_app

Deploying a Dash App on Heroku (Python)

This may be less about the universal how-to, and more about how I deployed mine. Which was not easy. So if you get frustrated, you are not alone. I gave up on multiple days after spending countless hours trying to figure out why the app was crashing.

FIRST THINGS FIRST

Make your app! I'm not going to go into detail on this piece. If you're looking up how to deploy something, chances are you have something to deploy.

SECOND THINGS SECOND - OR SOMETHING LESS REDUNDANT

Add the files in your root directory that heroku requires to deploy. My directory consists of the following (not saying this is all you'll need, but this is what worked for me - which my app is just a dash dashboard. Nothing special):

assets folder (for stylesheets and other media files)
app.py
the csv/data file
Procfile (the one-liner that tells heroku which web service you're using)
requirements.txt (the file that shows all the libraries needed to run you program)

A LITTLE DEEPER ON THE FILES YOU'RE LIKELY SAYING "HUH" TO

Procfile: this is literally a file (file type = file (not .txt. not anything) that says web: gunicorn app:server. That's it. Place it in the root directory, make sure the gunicorn library is installed with pip install gunicorn, make sure the gunicorn library is in your requirements.txt file and move on. This was the reason my app crashed btw. It wasn't installed and then it wasn't in the requirements text file.
requirements.txt: this is created with $ pip freeze > requirements.txt. Make sure you're in the right directory. This just creates a file that heroku will use when deploying your app and says "this is all the libraries this app needs to work".

CREATE AN ACCOUNT ON HEROKU AND DOWNLOAD THE CLI

Easy as that - create the account on heroku, and download the cli. The instructions to do this are on heroku.com. pro tip I first elected to use the minty console that they recommended, but it's weird and commands are different and i hate learning duplicate tools, so i went back and installed in using the windows command prompt. The only difference was they say you can't scroll back that far. Ah, I didn't need to scroll back that far to begin with.

NEXT LOGIN TO HEROKU USING CLI

heroku login will open a webpage, enter in your creds and close that tab. You should be logged in in console now.

RUN GIT STUFF

Also included on the heroku deploy tab.
Install git
Make your heroku directory
Run the remote command (i forget this command but it's on the deploy tab)
Initialize it git init
Add your first commit git add .
Commit your changes git commit -m 'first commit'
Push your code git push heroku master (assuming you are deploying on master and not some other branch
Lastly Scale dynos (which still confuses me, but needs to be done in order for the app to be live: heroku ps:scale web=1
Then open the webpage and bam. You did it. 
That's a high-level. But that's basically it.

LOGS CAN BE HELPFUL

If your app fails, heroku has some logs you can view to get and idea of what's wrong. Go to the view log option on your deploy on the Overview tab. You may also find it helpful to run heroku logs --tail which will show you a few ending lines of the logs. I kept getting an h10 error - google was helpful eventually.

HEROKU OR GITHUB

You can do both, Github might be the way to go because you can just push your code to github and then it's stored there as well and heroku will listen to all those changes. I just did the heroku approach.

Anyways, Hope this helps. Best of luck!
