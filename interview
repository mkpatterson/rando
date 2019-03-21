
#Created for Nebulous review by Matthew K. Patterson
#Sia Discord username "dataspoke"

import array, string
from itertools import izip

# Starting values
startAlpha = 3139
startBravo = 27
matches = 0

# Math values
facAlpha = 16807
facBravo = 48271
mod      = 2147483647

# Base-10 arrays
arrAlpha = array.array('i')
arrBravo = array.array('i')

# Binary lists
lisAlpha = []
lisBravo = []

# Building first array of decimal numbers, up to 40 million
def BuildArrayAlpha():
    while len(arrAlpha) <= 40000000:
        x = startAlpha * facAlpha
        y = x % mod
        if len(arrAlpha) == 40000000:
            return
        elif len(arrAlpha) == 0:
            arrAlpha.append(y)
        elif len(arrAlpha) < 40000000:
            xx = arrAlpha[-1] * facAlpha
            yy = xx % mod
            arrAlpha.append(yy)
BuildArrayAlpha()

# Building second array of decimal numbers, up to 40 million
def BuildArrayBravo():
    while len(arrBravo) <= 40000000:
        x = startBravo * facBravo
        y = x % mod
        if len(arrBravo) == 40000000:
            return      
        elif len(arrBravo) == 0:
            arrBravo.append(y)
        elif len(arrBravo) < 40000000:
            xx = arrBravo[-1] * facBravo
            yy = xx % mod
            arrBravo.append(yy)
BuildArrayBravo()

# Converts decimal numbers from array into binary, slices out the 
# least significant 16 bits, appends the output to new list
def BinaryConverter(x, y):
    for i in x:
        z = format(i, '032b')
        sl = z.__getslice__(16, 40)
        y.append(sl)

BinaryConverter(arrAlpha, lisAlpha)
BinaryConverter(arrBravo, lisBravo)

# Correlates the two binary lists and counts the number of matching pairs
def Correlator(x, y):
    for i, j in izip(x, y):
        global matches
        if i == j:
            matches += 1
            #Uncomment below to see raw matching pairs
            #print i, j

Correlator(lisAlpha, lisBravo)

print (str(matches) + ' matching pairs found!')
