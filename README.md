# EXP 1 : Linear and Circular Convolution

## AIM: 

 To perform Linear and Circular Convolution for two given sequence using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (Linear Convolution): 
```
clc;
clear;
// Input signal x[n] and impulse response h[n]
x = [1 1 1 1];
h = [1 2 3 4];
m = length(x);
n = length(h);
// Time axes for input and impulse response
a = 0:1:m-1;
b = 0:1:n-1;
// Plot input signal x[n]
subplot(3,1,1);
plot2d3(a, x);
xlabel('Time');
ylabel('Amplitude');
title('Input Signal x[n]');
// Plot impulse response h[n]
subplot(3,1,2);
plot2d3(b, h);
xlabel('Time');
ylabel('Amplitude');
title('Impulse Response h[n]');
// Perform convolution using direct formula method
L = m + n - 1; // Length of output signal
y = zeros(1, L); // Initialize output
for i = 1:L
 conv_sum = 0;
 for j = 1:i
 if (j <= m) & ((i - j + 1) <= n) then
 conv_sum = conv_sum + x(j) * h(i - j + 1);
 end
 end
 y(i) = conv_sum;
end
disp(y, 'Convolution Sum using Direct Formula Method =');
// Plot output signal y[n]
subplot(3,1,3);
c = 0:1:L-1; // Time axis for output
plot2d3(c, y);
xlabel('Time');
ylabel('Amplitude');
title('Output Signal y[n] = x[n] * h[n]');
```

## PROGRAM (Circular Convolution): 
```
clc;
clear;
// Input signal x[n]
x = [1 1 1 1];
n1 = 0 : length(x) - 1;
subplot(3,1,1);
plot2d3(n1, x);
xlabel('Time');
ylabel('Amplitude');
title('Input Sequence x[n]');
// Impulse response h[n]
h = [1 2 3];
n2 = 0 : length(h) - 1;
subplot(3,1,2);
plot2d3(n2, h);
xlabel('Time');
ylabel('Amplitude');
title('Impulse Sequence h[n]');
// Zero-padding to make lengths equal
N1 = length(x);
N2 = length(h);
N = max(N1, N2);
N3 = N1 - N2;
if N3 > 0 then
 h = [h, zeros(1, N3)];
else
 x = [x, zeros(1, abs(N3))];
end
disp(x, "Padded x[n] = ");
disp(h, "Padded h[n] = ");
// Circular convolution computation
y = zeros(1, N); // Initialize output
for n = 1:N
 for i = 1:N
 j = modulo(n - i, N);
 if j < 0 then
 j = j + N;
 end
 y(n) = y(n) + x(i) * h(j + 1); // +1 because Scilab is 1-indexed
 end
end
disp(y, "Circular Convolution y[n] = ");
// Plot circular convolution result
n = 0 : N - 1;
subplot(3,1,3);
plot2d3(n, y);
xlabel('Time');
ylabel('Amplitude');
title('Circular Convolution Result y[n]'); 

```

## OUTPUT (Linear Convolution):

<img width="756" height="579" alt="image" src="https://github.com/user-attachments/assets/acc3c8fe-b3f9-423a-93c9-6853f126d486" />


## OUTPUT (Circular Convolution):

<img width="1718" height="872" alt="image" src="https://github.com/user-attachments/assets/fa5dbf95-8b7d-4f15-b807-340317076111" />

## RESULT:
Thus,the Linear and Circular Convolution is verified
