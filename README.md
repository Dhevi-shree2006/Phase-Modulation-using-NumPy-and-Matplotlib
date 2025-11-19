# Phase-Modulation-using-NumPy-and-Matplotlib

### Aim
To implement and analyze phase modulation (PM) using Python's NumPy and Matplotlib libraries.   
### Apparatus Required
1.	Software: Python with NumPy and Matplotlib libraries  
2.	Hardware: Personal Computer Theory  
Phase Modulation (PM) is a technique where the phase of the carrier wave is varied in proportion to the instantaneous amplitude of the input signal (message signal). Unlike frequency modulation, where the frequency is varied, in phase modulation, the phase angle of the carrier wave changes with the amplitude of the message signal.  

The general form of a PM signal can be represented as:


<img width="306" height="241" alt="image" src="https://github.com/user-attachments/assets/b8d2db63-afe0-4bd8-8826-efc89a111423" />

### Algorithm

1.	Initialize Parameters:  
o	Set values for carrier amplitude (AcA_cAc), carrier frequency (fcf_cfc), message frequency (fmf_mfm), sampling frequency, and phase deviation sensitivity (kpk_pkp).  
2.	Generate Time Axis:  
o	Create a time vector for the signal duration based on the sampling frequency.  
3.	Generate Message Signal:  
o	Define the message signal as a cosine wave.  
4.	Generate PM Signal:  
o	Apply the PM modulation formula to obtain the modulated signal.  
5.	Plot the Signals:   
o	Use Matplotlib to plot the message signal, carrier signal, and phase-modulated signal.  


### Program
```
clc;
clear;
close;
Am = 6.1;          // Amplitude of message signal
fm = 563;          // Frequency of message signal (Hz)
Ac = 12.2;         // Amplitude of carrier signal
fc = 5630;         // Frequency of carrier signal (Hz)
mu = 0.5;          // Modulation index (phase deviation sensitivity)
fs = 56300;        // Sampling frequency (Hz)
t = 0:1/fs:0.01;   
m = Am * cos(2 * %pi * fm * t);   // Message signal
c = Ac * cos(2 * %pi * fc * t);   // Carrier signal

// -------------------- Step 4: Generate Phase Modulated Signal --------------------
kp = mu;                          // Phase deviation sensitivity
s = Ac * cos(2 * %pi * fc * t + kp * m);  // Phase modulated signal

// -------------------- Step 5: Plot the Signals --------------------
subplot(3,1,1);
plot(t, m);
title('Message Signal m(t)');
xlabel('Time (s)');
ylabel('Amplitude');

subplot(3,1,2);
plot(t, c);
title('Carrier Signal c(t)');
xlabel('Time (s)');
ylabel('Amplitude');

subplot(3,1,3);
plot(t, s);
title('Phase Modulated Signal s(t)');
xlabel('Time (s)');
ylabel('Amplitude');

// -------------------- Step 6: (Optional) Simple Demodulation --------------------
// Approximate demodulation using differentiation and envelope detection
diff_s = diff(s);                 // Differentiate PM signal
demod = abs(hilbert(diff_s));    // Envelope detection

figure;
plot(t(1:$-1), demod);
title('Demodulated Signal (Approximation)');
xlabel('Time (s)');
ylabel('Amplitude');
```



### Tabulation
<img width="1080" height="1077" alt="image" src="https://github.com/user-attachments/assets/c8d594f1-f26d-47d4-9fd1-49787ab2482d" />



### Output
<img width="759" height="722" alt="image" src="https://github.com/user-attachments/assets/81d17e53-2c8a-4004-9699-c8bd928447cf" />
<img width="754" height="721" alt="image" src="https://github.com/user-attachments/assets/e4e30ed1-3a4e-4190-b322-4b6d7ef9678b" />




### Result
The message signal, carrier signal, and phase-modulated (PM) signal will be displayed in separate plots. The modulated signal will show phase variations corresponding to the amplitude of the message signal.

