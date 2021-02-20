## CS290

In order to access your Node server, please follow these steps:
1. Connect to OSU's VPN   
    - Open the Cisco AnyConnect Secure Mobility Client App        
    - Enter `vpn.oregonstate.edu` and click connect   
    - Enter your OSU username and password in the login window and click "Login". 
    - Complete the Duo two-step login process.   
    
2. SSH into OSU's flip servers using VS Code.    
    - If you need to change flip servers type `ssh flip1`     
3. The Node files are contained within your CS290 folder on flip. Make any changes you would like.   
4. Set up an alias for forever. This will simply shorten how much you have to type each time you want to invoke forever by replacing the word forever in any command with ./node_modules/forever/bin/forever. Depending on the shell your user is currently running, this process uses the bash shell.     
    - Open your .bashrc file by typing nano ~/.bashrc       
    - Go to the bottom of the file and add a new line       
    - On this line type alias forever="./node_modules/forever/bin/forever"   
    - Save the file and exit      
    - Reload your bash shell settings by typing source ~/.bashrc or by logging out and back in     
5. Your server is up and running on port 4686. It can be accessed via the following link: http://flip1.engr.oregonstate.edu:4686 while you are connected to OSU's VPN.

### Notes on Forever    
1) Always remember that forever can only be run from a folder where the forever node module has been installed.
2) To start a forever process type forever start [app name] [optional port number if not specified in app]. E.g., forever start app.js 5678 (a common mistake is to forget the "start" keyword)
3) To view currently running processes you can type forever list
4) To kill a running application, take the id from the desired application in the output of (3) (it's toward the beginning of the line and in brackets) and type forever stop [process id]. E.g., forever stop 1
5) Alternatively to (4), you could just stop all of the processes you have running by running forever stopall
6) Forever suppresses and redirects errors to a logfile in your ~/.forever/ directory (the ~ means your user's home directory; i.e. the directory you're in when you first log into flip). These logfiles are unique to each forever instance you start and consist of a random 4-character name. To determine which logfile pertains to your application of interest you can either (a) run ls -al and examine the last modified time of each file or (b) run forever list and examine the "logfile" column of the output, taking note of the name of the file at the end of the path. From there, you can use your favorite text editor to open and examine the logfile. If you don't want to bother with logfiles, just run your application with node app.js until you believe it's in its final state.


