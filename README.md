# -Frequency-Modulation-and-Demodulation-using-NumPy-and-Matplotlib-

__Aim:__

To implement and analyze frequency modulation (FM) using Python's NumPy and Matplotlib libraries.

__Apparatus Required:__ 

1. Software: Python with NumPy and Matplotlib libraries
   
2. Hardware: Personal Computer

 
__Theory:__

Frequency Modulation (FM) is a method of transmitting information over a carrier wave by varying its 
frequency in accordance with the amplitude of the input signal (message signal). The frequency of the carrier 
wave is varied according to the instantaneous amplitude of the message signal.

__Algorithm:__

1. Initialize Parameters: Set the values for carrier frequency, message frequency, sampling frequency, and 
   frequency deviation.
   
2. Generate Time Axis: Create a time vector for the signal duration.
    
3. Generate Message Signal: Define the message signal as a cosine wave.
    
4. Compute the Integral of the Message Signal: Calculate the integral of the message signal over time.
    
5. Generate FM Signal: Apply the FM modulation formula to obtain the modulated signal.
 
6. Plot the Signals: Use Matplotlib to plot the message signal, carrier signal, and modulated signal.

__Programme:__
```
import numpy as np
import matplotlib.pyplot as plt

# Parameters
Am = 10.1      # Message amplitude
Ac =  20.2      # Carrier amplitude
fm = 580         # Message frequency
fc = 5800         # Carrier frequency
kf = 200          # Frequency sensitivity
fs = 200000       # Sampling frequency (high for smooth FM)
t = np.arange(0, 0.01, 1/fs)

# Message Signal
message = Am * np.cos(2 * np.pi * fm * t)

# Carrier Signal
carrier = Ac * np.cos(2 * np.pi * fc * t)

# FM Modulated Signal (correct formula)
beta = (kf * Am) / fm
fm_signal = Ac * np.cos(2*np.pi*fc*t + beta * np.sin(2*np.pi*fm*t))

# FM Demodulation (Differentiate + Envelope)
temp = np.diff(fm_signal)            # differentiate
demodulated = np.abs(temp)           # envelope
t2 = t[:-1]                           # time adjust

# Plotting
plt.figure(figsize=(12,10))

plt.subplot(4,1,1)
plt.plot(t, message)
plt.title("Message Signal")
plt.xlabel("Time")
plt.ylabel("Amplitude")

plt.subplot(4,1,2)
plt.plot(t, carrier)
plt.title("Carrier Signal")
plt.xlabel("Time")
plt.ylabel("Amplitude")

plt.subplot(4,1,3)
plt.plot(t, fm_signal)
plt.title("FM Modulated Signal")
plt.xlabel("Time")
plt.ylabel("Amplitude")

plt.subplot(4,1,4)
plt.plot(t2, demodulated)
plt.title("FM Demodulated Signal")
plt.xlabel("Time")
plt.ylabel("Amplitude")

plt.tight_layout()
plt.show()
```
__TABULATION__:

![WhatsApp Image 2025-11-26 at 00 30 26_aba7476c](https://github.com/user-attachments/assets/7504e7a6-de00-40f3-8612-792da5d0a4fd)


__Output:__

![WhatsApp Image 2025-11-26 at 00 27 04_9ba0a20d](https://github.com/user-attachments/assets/88f24305-cb04-4add-8d72-95accfc8f5ea)

__Result:__

![WhatsApp Image 2025-11-26 at 00 30 32_f3ffbaab](https://github.com/user-attachments/assets/09b66682-60cc-4645-b3e9-244f2e50716b)
