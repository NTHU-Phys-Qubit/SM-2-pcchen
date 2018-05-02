

```python
#Q1-1
from random import randint
sides= randint(1,7) ## determind the sides
N=randint(1,7) ## determind the number of the dice

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

    Number of sides =  7
    Number of trials =  10000
    Number of dice =  5
    [ 5.  6.  7.  8.  9. 10. 11. 12. 13. 14. 15. 16. 17. 18. 19. 20. 21. 22.
     23. 24. 25. 26. 27. 28. 29. 30. 31. 32. 33. 34. 35.]
    [  25.   36.   49.   64.   81.  100.  121.  144.  169.  196.  225.  256.
      289.  324.  361.  400.  441.  484.  529.  576.  625.  676.  729.  784.
      841.  900.  961. 1024. 1089. 1156. 1225.]
    [0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0.
     0. 0. 0. 0. 0. 0. 0.]
    the result of rolls
    [[1416. 1432. 1410. 1400. 1466. 1442. 1434.]
     [1435. 1440. 1447. 1390. 1374. 1445. 1469.]
     [1433. 1420. 1473. 1371. 1431. 1430. 1442.]
     [1463. 1438. 1380. 1438. 1443. 1368. 1470.]
     [1427. 1393. 1477. 1456. 1385. 1416. 1446.]]
    the result of rolls of sum
    [  0.   3.  15.  18.  33.  85. 110. 189. 290. 412. 493. 597. 696. 804.
     844. 825. 806. 798. 727. 599. 544. 351. 295. 181. 107. 100.  43.  24.
       5.   5.   1.]
    the simulation  mean,variance,standard deviation of the sum = 20.0129 20.22313359000009 4.497013852547053
    the theoretical mean,variance,standard deviation of the sum = 20.0 20.0 4.47213595499958
    Elapsed time = 0.09021873385187246
    


```python
#Q1-2
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
    #print(rep) ## the number of sum
    #print(repsq) ## the square of the number of sum
    sofhis = np.zeros(N*sides-N+1) ## the number of trials of the sum
    #print(sofhis)
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
    #print("the result of rolls")
    #print(histogram)
    #print("the result of rolls of sum")
    #print(sofhis)
    print("the simulation  mean,variance,standard deviation of the sum =" , me,var,dev)
    print("the theoretical mean,variance,standard deviation of the sum =" ,0.5*(sides+1)*N,float(N*(sides**(2)-1))/12,(float(N*(sides**(2)-1))/12)**(0.5))
    c2=time.clock()
    print("Elapsed time =", c2-c1)
def run():
    OneDieS_np(10000, 10,2)
    OneDieS_np(100000, 10,2)
    OneDieS_np(1000000, 10,2)
    OneDieS_np(10000, 20,10)
    OneDieS_np(100000, 20,10)
    OneDieS_np(1000000, 20,10)

run()
```

    Number of sides =  10
    Number of trials =  10000
    Number of dice =  2
    the simulation  mean,variance,standard deviation of the sum = 10.9291 16.42047319000001 4.0522183048300855
    the theoretical mean,variance,standard deviation of the sum = 11.0 16.5 4.06201920231798
    Elapsed time = 0.0384229253177466
    Number of sides =  10
    Number of trials =  100000
    Number of dice =  2
    the simulation  mean,variance,standard deviation of the sum = 11.02897 16.58615073910002 4.072609819157738
    the theoretical mean,variance,standard deviation of the sum = 11.0 16.5 4.06201920231798
    Elapsed time = 0.3542499410143307
    Number of sides =  10
    Number of trials =  1000000
    Number of dice =  2
    the simulation  mean,variance,standard deviation of the sum = 11.002143 16.507312407550998 4.062919197762983
    the theoretical mean,variance,standard deviation of the sum = 11.0 16.5 4.06201920231798
    Elapsed time = 3.655084200918168
    Number of sides =  20
    Number of trials =  10000
    Number of dice =  10
    the simulation  mean,variance,standard deviation of the sum = 105.0655 328.11280975000045 18.113884446744173
    the theoretical mean,variance,standard deviation of the sum = 105.0 332.5 18.23458252881047
    Elapsed time = 0.16743144441798563
    Number of sides =  20
    Number of trials =  100000
    Number of dice =  10
    the simulation  mean,variance,standard deviation of the sum = 105.1071 333.213949590001 18.254148832251833
    the theoretical mean,variance,standard deviation of the sum = 105.0 332.5 18.23458252881047
    Elapsed time = 1.6255366602837
    Number of sides =  20
    Number of trials =  1000000
    Number of dice =  10
    the simulation  mean,variance,standard deviation of the sum = 104.961707 333.1809086461508 18.25324378421958
    the theoretical mean,variance,standard deviation of the sum = 105.0 332.5 18.23458252881047
    Elapsed time = 14.167470828983085
    


```python
#Q1-3
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
    #print(rep) ## the number of sum
    #print(repsq) ## the square of the number of sum
    sofhis = np.zeros(N*sides-N+1) ## the number of trials of the sum
    #print(sofhis)
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
    #print("the result of rolls")
    #print(histogram)
    #print("the result of rolls of sum")
    #print(sofhis)
    print("the simulation  mean,variance,standard deviation of the sum =" , me,var,dev)
    print("the theoretical mean,variance,standard deviation of the sum =" ,0.5*(sides+1)*N,float(N*(sides**(2)-1))/12,(float(N*(sides**(2)-1))/12)**(0.5))
    c2=time.clock()
    print("Elapsed time =", c2-c1)
def run():
    OneDieS_np(10000,2,10)
    OneDieS_np(10000,2,40)
    OneDieS_np(10000,2,70)
    OneDieS_np(10000,2,100)

run()
```

    Number of sides =  2
    Number of trials =  10000
    Number of dice =  10
    the simulation  mean,variance,standard deviation of the sum = 14.9902 2.4111039599999913 1.5527729904915242
    the theoretical mean,variance,standard deviation of the sum = 15.0 2.5 1.5811388300841898
    Elapsed time = 0.14103466899280193
    Number of sides =  2
    Number of trials =  10000
    Number of dice =  40
    the simulation  mean,variance,standard deviation of the sum = 60.021 9.711358999999902 3.116305344474431
    the theoretical mean,variance,standard deviation of the sum = 60.0 10.0 3.1622776601683795
    Elapsed time = 0.4949378070308512
    Number of sides =  2
    Number of trials =  10000
    Number of dice =  70
    the simulation  mean,variance,standard deviation of the sum = 105.0404 17.56016783999803 4.190485394318662
    the theoretical mean,variance,standard deviation of the sum = 105.0 17.5 4.183300132670378
    Elapsed time = 0.9203848309617797
    Number of sides =  2
    Number of trials =  10000
    Number of dice =  100
    the simulation  mean,variance,standard deviation of the sum = 149.9896 25.329091840001638 5.032801589572316
    the theoretical mean,variance,standard deviation of the sum = 150.0 25.0 5.0
    Elapsed time = 1.3308277942711584
    


```python
#Q1-3 ANS:寬度與標準偏差成正比。從結果中可以發現，隨著骰子數量的增加，分佈寬度增加。
```
