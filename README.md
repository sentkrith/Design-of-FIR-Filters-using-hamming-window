# Design-of-FIR-Filters-using-hamming-window

# DESIGN OF LOW PASS FIR DIGITAL FILTER 

# AIM: 
          
  To generate design of high pass FIR digital filter using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM 
```
clc;
clear;
close;

// FIR Low Pass Filter Design using Fourier Series Method
// Using Hamming Window

// Step 1: Input specifications
M = input("Enter the Odd Filter Length = ");          // e.g., 21
Wc = input("Enter the Digital Cutoff Frequency (in radians) = ");  // e.g., 0.4*%pi

alpha = (M - 1) / 2;    // Center value

// Step 2: Compute ideal impulse response (sinc function)
for n = 1:M
    if (n == alpha + 1) then
        hd(n) = Wc / %pi;   // center sample (sinc(0))
    else
        hd(n) = sin(Wc * ((n - 1) - alpha)) / (((n - 1) - alpha) * %pi);
    end
end

// Step 3: Define Hamming Window
for n = 1:M
    W(n) = 0.54 - (0.46 * cos((2 * %pi * (n - 1)) / (M - 1)));
end

// Step 4: Apply window to impulse response
h = hd .* W;
disp(h, "Filter Coefficients are:");

// Step 5: Compute Frequency Response
[hzm, fr] = frmag(h, 256);  // 256-point frequency response

// Step 6: Plot magnitude and magnitude (dB)
subplot(2,1,1);
plot(2*fr, hzm);
xlabel("Normalized Digital Frequency (×π rad/sample)");
ylabel("Magnitude");
title("Frequency Response of FIR LPF using Hamming Window");

subplot(2,1,2);
hzm_dB = 20 * log10(hzm);
plot(2*fr, hzm_dB);
xlabel("Normalized Digital Frequency (×π rad/sample)");
ylabel("Magnitude (dB)");
title("Frequency Response of FIR LPF using Hamming Window (in dB)");

```

# OUTPUT

<img width="1176" height="670" alt="image" src="https://github.com/user-attachments/assets/5078b3a5-ac05-41da-9264-3e10bfbc9834" />

# RESULT
Thus, generate design of high pass FIR digital filter using SCILAB are verified
