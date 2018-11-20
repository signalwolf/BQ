# LTE Database
LTE wireless system is an very complex system. So, your phone connection to network is under some 
regulation. This is call LTE specification, it defines what your phone should do under almost all 
scenario. The is 1000 + IEs and it can be combined in different ways. In another word, their would be
billions of combinations.

So, it is not possible that all those combinations appear in real live. The network designer like VzW 
ATT will choice the best one fit their requirement. It maybe only 100 different combinations for each 
network. 

I start this project because a lot of my enhancement proposal been rejected due to system team think 
my proposal could have side effect under some specific combination and I can't argue with them saying 
"hey man, I never see this combination in live network before". So, I thinking how to prove that, Qualcomm
have huge number of field test engineer perform live network globally and generate 100 GB logs everyday.
Within those logs, it should have some information. 

Then I started to looking into those logs and make up a list of IE we wanted to tracking. So, we process 
the logs and automatic covert it to excel then update to the database. 

Right now, people will look for the database during the design and it is a really helpful tools across 
the team. 

### My role: 
I take the leadership in this projects. We have three people, one guy is using PHH to write the webpage,
another guy is set up the server using XAMPP. I write the entire software from take logs and convert to
txt files, filter the specific IEs and update the database. 

Also, I handled the save method for this database.


### Fun parts:
After 2 -3 years, the saving method suddenly not working. But if you filter some of the IEs, the save 
function still works. It sounds a real weird question, right? After debug, I found that the save func 
could output an Excel using python module xlwt and Excel have an limitation on number of columns. It 
can't handle more than 256 columns. So, if the output entities is more than 256, issue occurs but if 
you filter the IEs, then the entities goes to less than 256, so the issue disappear.
Our solution is change it to CSV, csv is pretty much like txt files. So, it can have unlimited output. 
That's weird and funnest mistake I ever made. 

### 