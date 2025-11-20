### Design-of-FIR-Filters-using-hamming-window
### DESIGN OF LOW PASS FIR DIGITAL FILTER 

### AIM:       
  To generate design of high pass FIR digital filter using SCILAB 

### APPARATUS REQUIRED: 
  PC Installed with SCILAB 

### PROGRAM 
//LPF
```
clc;
clear;
close;

M = input('Enter the Odd Filter Length = ');
Wc = input('Enter the Digital Cut off frequency (in radians) = ');

alpha = (M - 1) / 2; // Center value

// Ideal Low Pass filter coefficients
for n = 1:M
    if (n == alpha + 1) then
        hd(n) = Wc / %pi;   // center tap
    else
        hd(n) = sin(Wc * ((n - 1) - alpha)) / (((n - 1) - alpha) * %pi);
    end
end

// Hamming Window
for n = 1:M
    W(n) = 0.54 - (0.46 * cos((2 * %pi * (n - 1)) / (M - 1)));
end

// Apply window to ideal filter
h = hd .* W;
disp(h, 'Filter Coefficients are:');

// Frequency response
[hzm, fr] = frmag(h, 256);

subplot(2, 1, 1);
plot(2 * fr, hzm);
xlabel('Normalized Digital Frequency w');
ylabel('Magnitude');
title('Frequency Response of FIR LPF using Hamming Window');

hzm_dB = 20 * log10(hzm);
subplot(2, 1, 2);
plot(2 * fr, hzm_dB);
xlabel('Normalized Digital Frequency w');
ylabel('Magnitude (dB)');
title('Frequency Response of FIR LPF using Hamming Window');

```
//HPF
```
clc;
clear;
close;

M = input('Enter the Odd Filter Length = ');
Wc = input('Enter the Digital Cut off frequency (in radians) = ');

alpha = (M - 1) / 2; // Center value

// Ideal High Pass filter coefficients
for n = 1:M
    if (n == alpha + 1) then
        hd(n) = 1 - (Wc / %pi);
    else
        hd(n) = -sin(Wc * ((n - 1) - alpha)) / (((n - 1) - alpha) * %pi);
    end
end

// Hamming Window
for n = 1:M
    W(n) = 0.54 - (0.46 * cos((2 * %pi * (n - 1)) / (M - 1)));
end

// Apply window to ideal filter
h = hd .* W;
disp(h, 'Filter Coefficients are:');

// Frequency response
[hzm, fr] = frmag(h, 256);

subplot(2, 1, 1);
plot(2 * fr, hzm);
xlabel('Normalized Digital Frequency w');
ylabel('Magnitude');
title('Frequency Response of FIR HPF using Hamming Window');

hzm_dB = 20 * log10(hzm);
subplot(2, 1, 2);
plot(2 * fr, hzm_dB);
xlabel('Normalized Digital Frequency w');
ylabel('Magnitude (dB)');
title('Frequency Response of FIR HPF using Hamming Window');

```

### OUTPUT
<img width="1458" height="1018" alt="hamming" src="https://github.com/user-attachments/assets/45264f9f-8835-4aaa-8e33-3623dcfe68af" />
![WhatsApp Image 2025-11-20 at 13 16 08_d0aafea8](https://github.com/user-attachments/assets/084403c8-aaf7-4c1f-88a2-7e630bf3c6e7)



### RESULT
Design-of-FIR-Filters-using-hanning-window using SCILAB executed successfully.
