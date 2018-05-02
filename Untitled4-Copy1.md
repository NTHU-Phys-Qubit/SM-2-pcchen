

```python
from random import randint
sides= randint(1,10) ## determind the sides
N=randint(1,10) ## determind the number of the dice

import random
import time
import numpy as np

def OneDieS_np(trials, sides,N):
    c1=time.clock()
    print("Number of sides = ", sides)
    print("Number of trials = ", trials)
    print("Number of dice = ", N)
    rep = np.ones(N*sides-N+1)*(N-1)
    repsq = np.zeros(N*sides-N+1)
    for c in range(0,len(rep)):
        rep[c] = rep[c]+(c+1)
    for a in range(0,len(repsq)):
        repsq[a] = rep[a]**(2)
    print(rep) ## the number of sum
    print(repsq) ## the square of the number of sum
    sofhis = np.zeros(N*sides-N+1) ## the number of trials of the sum
    print(sofhis)
    histogram = np.zeros((N , sides))
    r = 0
    for t in range(trials):
        z = 0
        for i in range(0,N):
            r = int(np.random.random()*sides)
            histogram[i,r] = histogram[i,r] + 1
            z = z + r
        sofhis[z] = sofhis[z]+1
    me = 0 ## mean
    for h in range(0,len(rep)):
        me = me + rep[h]*sofhis[h]
    me = float(me)/trials 
    var = 0 ## variance
    for h in range(0,len(repsq)):
        var = var + repsq[h]*sofhis[h]
    var = float(var)/trials-me**(2)
    dev = var**(0.5) ## standard deviation
    print("the result of rolls")
    print(histogram)
    print("the result of rolls of sum")
    print(sofhis)
    print("the simulation  mean,variance,standard deviation of the sum =" , me,var,dev)
    print("the theoretical mean,variance,standard deviation of the sum =" ,0.5*(sides+1)*N,float(N*(sides**(2)-1))/12,(float(N*(sides**(2)-1))/12)**(0.5))
    c2=time.clock()
    print("Elapsed time =", c2-c1)
def run():
    OneDieS_np(10000, sides,N)
    

run()
```

    Number of sides =  3
    Number of trials =  10000
    Number of dice =  5
    [ 5.  6.  7.  8.  9. 10. 11. 12. 13. 14. 15.]
    [ 25.  36.  49.  64.  81. 100. 121. 144. 169. 196. 225.]
    [0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0.]
    the result of rolls
    [[3330. 3374. 3296.]
     [3271. 3344. 3385.]
     [3338. 3273. 3389.]
     [3327. 3293. 3380.]
     [3382. 3280. 3338.]]
    the result of rolls of sum
    [  38.  204.  603. 1222. 1866. 2042. 1919. 1259.  603.  201.   43.]
    the simulation  mean,variance,standard deviation of the sum = 10.014 3.306604000000007 1.818406995147128
    the theoretical mean,variance,standard deviation of the sum = 10.0 3.3333333333333335 1.8257418583505538
    Elapsed time = 0.07025477072895114
    
