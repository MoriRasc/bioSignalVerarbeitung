---
layout: default
title: Frequenzspektrum, DFT und FFT
---

# Frequenzspektrum, DFT und FFT

Erstelle basierend auf der mathematischen Formel für die DFT und iDFT zwei Python-Funktionen, um die DFT und iDFT eines gegebenen Signals 
x zu berechnen.

\[ 
X[k] = \sum_{n=0}^{N-1} x[n] \, e^{-j \tfrac{2\pi}{N}kn}, \quad k = 0, 1, \dots, N-1 
\]

\[
x[n] = \tfrac{1}{N} \sum_{k=0}^{N-1} X[k] \, e^{j \tfrac{2\pi}{N}kn}, \quad n = 0, 1, \dots, N-1
\]


**📝  Aufgabe 1: Verarbeitungszeit**

Für ein gegebenes Signal x: Stelle das Signal grafisch dar, berechne die Verarbeitungszeit für die selbst erstellte DFT-Funktion, die `numpy.fft()`-Funktion und die `scipy.fft()` -Funktion.


```python

import matplotlib.pyplot as plt
import numpy as np
import time
from scipy.fft import fft, fftfreq
import cmath
import math
#function to calculate the dft
def DFT(x): 
   
    return X

    


#iDFT

def iDFT(X):
    
    return x

# sampling rate
fs = 100
# sampling interval
ts = 1.0/fs
t = np.arange(0,1,ts)

freq = 1
x = 3*np.sin(2*np.pi*freq*t)

freq1 = 4
x += np.sin(2*np.pi*freq1*t)

freq2 = 7   
x += 0.5* np.sin(2*np.pi*freq2*t)

plt.figure(figsize = (8, 6))
plt.plot(t, x, 'r')
plt.xlabel('Zeit (s)')
plt.ylabel('Amplitude (V)')
plt.show()



#calculate computing time


print(f"Computation time for DFT: {end_time - start_time:.6f} seconds")
print(f"Computation time for Numpy FFT: {end_time1 - start_time1:.6f} seconds")
print(f"Computation time for Scipy FFT: {end_time2 - start_time2:.6f} seconds")


```

**📝  Aufgabe 2: Frequenzspektrum**

Berechne für das gegebene Signal die Frequenzen des Frequenzspektrums (bis $f_s$) und stelle die DFT-Ergebnisse entsprechend den berechneten Frequenzen grafisch dar.
- Warum erhalten wir am Anfang und am Ende des Spektrums die gleichen Werte?


```python
# calculate the frequency
N = len(X)
n = np.arange(N)
T = N/fs
freq = n/T 

plt.figure(figsize = (8, 6))
plt.stem(freq, abs(X), 'b', \
         markerfmt=" ", basefmt="-b")
plt.xlabel('Frequenz (Hz)')
plt.xlim(0, fs)
plt.title('Discrete Fourier Transform (DFT) des Signals x(t)')
plt.ylabel('DFT Amplitude (V²/Hz)')
plt.show()# resample the signal with a different sampling rate
 
```

## Dezimierung and Interpolation

Um die Signalverarbeitung effizienter zu gestalten, muss die Abtastrate eines Signals manchmal geändert werden. Das analoge Signal erneut mit einer höheren oder niedrigeren Frequenz abzutasten oder das vorhandene Signal zunächst in ein analoges Signal umzuwandeln und es dann mit einer anderen Abtastrate neu abzutasten, kann aufwendig sein. Daher ist die effizienteste Methode, das vorhandene digitale Signal zu dezimieren (Downsampling) oder zu interpolieren (Upsampling).

**📝  Aufgabe 3: Downsampling**

Downsample das gegebene Signal x um den Faktor 10, berechne und stelle das Frequenzspektrum (bis fs/20) grafisch dar und rekonstruiere sowie visualisiere das Signal durch Anwendung der iDFT-Funktion.
- Was passiert? Warum?


```python
factor = 10
x1 = x
t1 = t


plt.figure(figsize = (8, 6))
plt.plot(t1, x1, 'b')
plt.xlabel('Zeit (s)')
plt.title('Dezimiertes Signal x(t)')
plt.ylabel('Amplitude(V)')
plt.show()

# calculate the DFT des input signal
X = DFT(x1)

# calculate the frequency
N1 = len(X)
n1 = np.arange(N1)
T1 = N1/(fs/factor)
freq1 = n1/T1 

plt.figure(figsize = (8, 6))
plt.stem(freq1, abs(X), 'b', \
         markerfmt=" ", basefmt="-b")
plt.xlabel('Frequenz (Hz)')
plt.xlim(0, fs/20)
plt.title('Discrete Fourier Transform (DFT) des Signals x(t)')
plt.ylabel('Amplitude (V²/Hz)')
plt.show()


# calculate the inverse DFT
x_reconstructed = iDFT(X)
# plot the reconstructed signal
plt.figure(figsize = (8, 6))
plt.plot(t1, x_reconstructed.real, 'g')
plt.plot(t, x, 'r--')
plt.xlabel('Zeit (s)')
plt.ylabel('Amplitude (V)')
plt.title('Rekonstruiertes Signal von from DFT')
plt.legend(['Rekonstruiertes Signal', 'Original Signal'])
plt.xlim(0, 1)
plt.show()

```

**📝  Aufgabe 4: Interpolation**

Interpoliere das gegebene Signal x um den Faktor 10, berechne und stelle das Frequenzspektrum grafisch dar und rekonstruiere sowie visualisiere das Signal durch Anwendung der iDFT-Funktion.
- Was passiert? 
- Warum?
- Was müssen wir tun?


```python
# resample the signal to a new time vector

factor = 10


x2 = 
t2 = 


plt.figure(figsize = (8, 6))
plt.plot(t2, x2, 'b')
plt.xlabel('Zeit (s)')
plt.title('x2(t2)')
plt.ylabel('Amplitude')
plt.show()

# calculate the DFT des input signal
X2 = DFT(x2)

# calculate the frequency
N2 = len(X2)
n2 = np.arange(N2)
T2 = N2/(fs*factor)
freq2 = n2/T2 

plt.figure(figsize = (8, 6))
plt.stem(freq2, abs(X2), 'b', \
         markerfmt=" ", basefmt="-b")
plt.xlabel('Frequenz (Hz)')
plt.xlim(0, fs*factor/2)
plt.title('Discrete Fourier Transform (DFT) des Signals x(t)')
plt.ylabel('Amplitude (V²/Hz)')
plt.show()


# calculate the inverse DFT
x_reconstructed = iDFT(X2)
# plot the reconstructed signal
plt.figure(figsize = (8, 6))
plt.plot(t2, x_reconstructed.real, 'g')
plt.plot(t, x, 'r--')
plt.xlabel('Time (s)')
plt.ylabel('Amplitude (V²/Hz)')
plt.title('Rekonstruiertes Signal von DFT')
plt.legend(['Rekonstruiertes Signal', 'Original Signal'])
plt.xlim(0, 1)
plt.show()
```
