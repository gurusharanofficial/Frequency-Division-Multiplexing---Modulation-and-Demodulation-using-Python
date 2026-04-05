# Frequency-Division-Multiplexing---Modulation-and-Demodulation-using-Python

__Aim__:

To generate an FDM signal by multiplexing multiple baseband message signals on different carrier frequencies, transmit (sum) them, optionally add channel noise, then recover each message by bandpass filtering and coherent demodulation in Python (Google Colab). Observe time & frequency domain signals and measure recovery quality.


__Apparatus Required__:

Google Colab (or any Python environment)

Python libraries: numpy, matplotlib, scipy (scipy.signal)


__Theory__:

FDM places different message signals in separate, non-overlapping frequency bands by modulating each message onto a distinct carrier frequency. The multiplexed signal is the sum of all modulated channels. At the receiver, bandpass filters (or tuned filters) isolate each channel; then each isolated carrier is demodulated (coherently multiplied by a synchronized carrier) and low-pass filtered to recover the original baseband.

__Procedure__:

1 — Imports and parameters

2 — Create message signals and carriers

3 — Modulate each message (standard AM DSB-SC) and form FDM signal

4 — Frequency domain (spectrum) of FDM signal

5 — (Optional) Add AWGN noise to FDM signal

6 — Receiver: isolate each channel with bandpass filter

7 — Demodulate each isolated channel (coherent) and low-pass filter to recover baseband

__Program__:
```
import numpy as np    
import matplotlib.pyplot as plt    
Am=14.2    
fm=523   
Ac=28.4    
fc=5230   
fs=52300    
b=5.9     
t=np.arange(0,2/fm,1/fs)    
m = np.cos(2 * np.pi * fm * t)    
c=np.cos(2*np.pi*fc*t)    
s = np.cos(2 * np.pi * fc * t + b * np.cos(2 * np.pi * fm * t))    

plt.subplot(3,1,1)     
plt.plot(t, m)     

plt.subplot(3,1,2)    
plt.plot(t,c)     

plt.subplot(3,1,3)      
plt.plot(t,s)
```
__Output__:

<img width="699" height="508" alt="Screenshot 2026-03-27 082825" src="https://github.com/user-attachments/assets/859c1b57-92f1-4491-b371-2f42f2997eb2" />

__Tabulation__:

<img width="1637" height="1532" alt="image" src="https://github.com/user-attachments/assets/9fe8caec-249e-451d-b3a8-74525c9f9a3a" />

__Result__:

The message signal, carrier signal, and frequency modulated (FM) signal will be displayed in separate plots. The modulated signal will show frequency variations corresponding to the amplitude of the message signal.
