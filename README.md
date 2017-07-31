# ProofOfWork
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
Created on Mon Jul 31 10:10:20 2017

@author: auqib
"""
import hashlib
import random
import time
import string
challenge='ABcvdkkk3545446'
def gen(ch=challenge,size =10):
    ans= ''.join(random.choice(string.ascii_lowercase+string.ascii_uppercase+string.digits) for x in range(size))
    atempt=ch+ans
    print(ans)
    return atempt,ans
hash = hashlib.sha256()
def attempt():
    Found= False
    start=time.time()
    while Found == False:
        atempt,ans=gen()
        at=atempt.encode('utf-8')
        hash.update(at)
        sol=  hash.hexdigest()
        if sol.startswith('000'):
            timetook=time.time() - start
            print(sol)
            print('Time ellapsed',timetook)
            Found = True
            print(ans)
attempt()
