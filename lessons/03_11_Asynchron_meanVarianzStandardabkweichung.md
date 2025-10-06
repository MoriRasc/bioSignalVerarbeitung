# Signale: Zeitbereich vs Frequenzbereich
Ein Signal beschreibt, wie sich ein Parameter auf einen anderen bezieht, beispielsweise der Weg in Bezug zur Zeit. Signale können entweder kontinuierlich (z.B. x(t), y(t)) oder diskret (z.B. x[n], y[n]) sein.

<img src="../attachments/zeitVsFreq.png" width="900">

## Signale im Zeitbereich
Im Zeitbereich werden die Werte eines Signals über einen bestimmten Zeitraum angegeben. Signale werden hier üblicherweise mit kleinen Buchstaben, wie y() oder y[], dargestellt. Die Analyse im Zeitbereich konzentriert sich auf Parameter wie Maximum- und Minimumwerte, den Mittelwert, die Standardabweichung, lokale Maxima und Nulldurchgänge. Je nach Fragestellung können zeit- und/oder amplitudenbasierte Analysen relevant sein.

## Signale im Frequenzbereich
Der Frequenzbereich beschreibt die Amplituden der erzeugten Sinus- und Kosinuswellen eines Signals. Signale in diesem Bereich werden typischerweise mit Großbuchstaben, wie Y() oder Y[], symbolisiert.

## Der Zusammenhang zwischen Zeit- und Frequenzbereich
Beide Darstellungen – Zeit- und Frequenzbereich – enthalten die gleichen Informationen, präsentieren diese aber auf unterschiedliche Weise. Eine Umwandlung zwischen diesen Darstellungen ist möglich und erfolgt hauptsächlich mittels der Fourier-Transformation.



## Typische Parameter eines Zeitbereichssignals sind zum Beispiel:

<img src="../attachments/zeit.png" width="900">

- Amplitude – maximale Auslenkung des Signals (z. B. in Volt)
- Mittelwert - gibt den durchschnittlichen Wert eines Signals über die Zeit an
- Standardabweichung - misst die Streuung der Werte um den Mittelwert
- Spitzenwert – maximale positive oder negative Auslenkung
- Periodendauer (bei periodischen Signalen) – Dauer eines Zyklus
- Offset (DC-Anteil) – Gleichspannungsanteil des Signals
- Effektivwert (RMS) – quadratischer Mittelwert, wichtig für Leistung
- Signalform – z. B. Sinus, Rechteck, Dreieck
- Anstiegszeit / Abfallzeit – Zeit, die das Signal braucht, um von einem niedrigen auf einen hohen Wert zu wechseln (oder umgekehrt)
- Duty Cycle (Tastverhältnis) - bei periodischen Rechteck- oder Puls-Signalen, wie lange das Signal während einer Periode "ein" (aktiv, high) ist, im Verhältnis zur gesamten Periodendauer.

Das folgende Signal ist gegeben:


```python
#In[1] Definition of Libraries and Variables
import statistics
import numpy as np
from matplotlib import pyplot as plt
from matplotlib import style
from scipy.signal import find_peaks
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import square
from scipy.ndimage import gaussian_filter1d
# Time vector
t = np.linspace(0, 10, 1000)

# Base signal: 4 oscillations → 4 maxima and 4 minima
base = np.sin(2 * np.pi * 4 * t / max(t))  # 4 cycles

# Amplitude envelope to vary max and min heights
envelope = 1 + 0.5 * np.sin(2 * np.pi * t / max(t))  # slow variation

# Final signal: modulated sine wave
signal = 2.5 + envelope * base

# Plot the signal
plt.style.use('default')
plt.figure(figsize=(12, 5))
plt.plot(t, signal, label="Signal", color='orange')
plt.title("Signal ")
plt.xlabel("Zeit (s)")
plt.ylabel("Spannung (V)")
plt.legend()
plt.grid(True)
plt.show()
```

**📝 Aufgabe 1:**

- Berechnen Sie mathematisch das Maximum und das Minimum der Funktion
- Zeichnen Sie die lokalen Maxima und Minima mit der Funktion `find_peaks` auf.



```python
# In[2] Find local maxima using the find_peaks function



# Plot the signal

```

**📝 Aufgabe 2:**

Gesucht: Mittelwert, Varianz, Standardabweichung, Max, Min

- Schreiben Sie eine Funktion, die diese Rechnungen ausführt ohne die eingebauten Funktionen von Python Bibliotheken zu verwenden

- Verwenden Sie dann die eingebauten Funktionen von Python Bibliotheken und vergleichen Sie den Wert

- Plotten Sie das Signal, Mittelwert, Lokale Max und Min und Max und Min in einem Plot



```python
#In[3]
#Mittelwert


#Varianz


#Standardabweichung


#Max


#Min


# Find the index of the maximum value in y

# Find the index of the minimum value in y


# Plot the signal


# Plotting the signal with the mean value line

```

Die folgende ideales Rechtecksignal ist gegeben:
- Amplitude: 1
- Offset: 0.5
- Periode: 0.2 s
- Duty cycle: 20%

Was ist der Unterschied zwischen einem idealen und einem realen Rechtecksignal? Was bedeutet das im Frequenzbereich?


```python
#In[4]
# Create an ideal square signal of amplitude 1 and offset 0.5
# with a period of 0.2 seconds and a duty cycle of 20%


# Time vector
t = np.linspace(0, 1, 1000)  # 1 second total duration, 1000 samples

# Signal parameters
amplitude = 1
offset = 0.5
period = 0.2
duty_cycle = 0.5  # percent

# Generate ideal square wave with specified duty cycle
raw_square = square(2 * np.pi * t / period, duty=duty_cycle)

# Scale to amplitude and offset
ideal_signal = (raw_square + 1) / 2 * amplitude + offset

# Plot the square signal
plt.figure(figsize=(10, 4))
plt.plot(t, ideal_signal, label="Rechtecksignal")
plt.xlabel("Zeit (s)")
plt.ylabel("Spannung (V)")
plt.title("Ideales Rechtecksignal")
plt.grid(True)
plt.legend()
plt.show()
```

**📝 Aufgabe 3:** 

Erzeuge und plotte ein nichtideales Rechtecksignal basierend auf die gegebenen Parametern.


```python
#In[5]
# Create a non ideal square signal of amplitude 1 and offset 0.5
# with a period of 0.2 seconds and a duty cycle of 20%


# Time vector
t = np.linspace(0, 1, 1000)  # 1 second total duration, 1000 samples

# Signal parameters
amplitude = 1
offset = 0.5
period = 0.2
duty_cycle = 0.5  # percent

# Generate ideal square wave with specified duty cycle
raw_square = square(2 * np.pi * t / period, duty=duty_cycle)

# Scale to amplitude and offset
ideal_signal = (raw_square + 1) / 2 * amplitude + offset

# Add non-ideal behavior: smooth the transitions
non_ideal_signal = 

# Plot the square signal
plt.figure(figsize=(10, 4))
plt.plot(t, non_ideal_signal, label="Rechtecksignal")
plt.xlabel("Zeit (s)")
plt.ylabel("Spannung (V)")
plt.title("Nichtideales Rechtecksignal")
plt.grid(True)
plt.legend()
plt.show()
```

**📝 Aufgabe 4:** 

Berechnen Sie die Anstiegs- und Abfallzeiten.


```python
#In[5] Calculate the rise and fall times


print("Anstiegszeiten / s:", rise_time)
print("Abfallzeiten / s:", rise_time)
```
