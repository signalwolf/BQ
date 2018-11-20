#目录
[Machine learning assisted wireless communication system design on HST](#Machine-learning-assisted-wireless-communication-system-design-on-HST)   
[The tuning method](#The-tuning-method)    
[fun parts](#fun-parts)    
[challenge parts](#challenge-parts)   


# Machine learning assisted wireless communication system design on HST
We are the LTE modem group, modem is the chipset help your phone to connected to LTE towers.
In wireless communication, the connection quality is highly related to the speed of movement. Just
image you running from one tower to another, it is not too hard to suffer any connection issue. 
But if you are on HST in China, then it is a problem because it moves 350 Km/h. 

So, LTE expert solve this by keep your phone in panic mode. Consistently see if there is an better 
LTE tower appear. If it appeared and looks very good at your monitoring window, your phone will switch
the tower.

But consistently looking for better tower is consume too much power, right? It can't be enabled all 
the time and the modem don't have speed information. So, the spec required those cells in HST signaling
an HSTflag to your phone and tell you if you are on HST or not.

Looks great. But the solution is overkilling the problem. Because network can be on the HST route but
the train on it can be moving really slow, like it is in HST station or it is making an S turn.

So, my solution is trying to solve this problem using machine learning. The features is all those 4G/LTE
measurement result, the target is to estimate the speed of modem movement. 
Initially, I tried to use linear regression to estimate the speed, although the RMS looks good on 
validation set but on test set it is quite not stable. To be honestly, I still don't know why and how 
to enhance it. 

So, later I decide to change the problem to an binary classification problem. Just two labels, 
HST or non HST. The result looks much better. After fine tune the model, we finally get our wireless
system design team happy and agreed to give an try in live network. 

Later I tried SVM, deep neuron network and RNN to solve the problem. But unfortunately the modem's 
compute power is really small. So deep neuron network and RNN not get implemented, otherwise your phone
could have much better performance.

### The tuning method
Cross validation. 

### Fun parts: 
everyone in system team is really into their field, so they don't have too many info in machine learning. The first time I told them, they think it is not possible to do it because they think
it must consume lots of power and memories. But since we are using the logistic regression, it is just 
few adding and multiply, it really not a big deal. In the memories side, they think the average and variation
calculation must compute based on saving those data to memory, then I present them with the moving average
and moving variations. 
### Challenge parts: 
The challenge part is clean the data, all the project I did before is cleaned data, so you don't care about the missing data, category data. So, that's the first challenge thing I meet; The
other parts is you are doing this thing by your own, their is no teacher to tell you, hey Xu, this part 
is wrong. Actually, this is another reason why I wanted to join your company, I can learn, grow and have fun
5;  
