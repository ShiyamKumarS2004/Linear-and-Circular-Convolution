# EXP 1 : Linear and Circular Convolution

## AIM: 

 To perform Linear and Circular Convolution for two given sequence using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (Linear Convolution): 
```clear;
clc;
close;
x = [1 1 2 1];
h = [1 2 3 4];
m = length(x);
n = length(h);
N = m + n - 1;
y = zeros(1, N);
for i = 1:N
    sum_val = 0;
    for j = 1:i
        if (j <= m) & ((i - j + 1) <= n) then
            sum_val = sum_val + x(j) * h(i - j + 1);
        end
    end
    y(i) = sum_val;
end
nx = 0:m-1;      
nh = 0:n-1;      
ny = 0:N-1;      
scf(0);
subplot(3,1,1);
plot2d3(nx, x, style=2);    // stem plot
xlabel("Time"); ylabel("Amplitude");
title("Graphical Representation of Input Signal X");
subplot(3,1,2);
plot2d3(nh, h, style=5);
xlabel("Time"); ylabel("Amplitude");
title("Graphical Representation of Impulse Signal h");
subplot(3,1,3);
plot2d3(ny, y, style=3);
xlabel("Time"); ylabel("Amplitude");
title("Graphical Representation of Output Signal y");
```


## PROGRAM (Circular Convolution): 
```clear; 
clc; 
close;
x = [1 1 3 1];
h = [1 2 3.1];
m = length(x);
n = length(h);
N = max(m, n);
if m < N then x($+1:N) = 0; end
if n < N then h($+1:N) = 0; end
y = zeros(1, N);
for k = 1:N
    s = 0;
    for j = 1:N
        idx = 1 + modulo(k - j + N, N);
        s = s + x(j) * h(idx);
    end
    y(k) = s;
end
disp(y, "y (circular) =");
naxis = 0:N-1;
scf(0);
subplot(3,1,1);
plot2d3(naxis, x);
xlabel("n"); ylabel("x(n)");
title("Input x(n)");
subplot(3,1,2);
plot2d3(naxis, h);
xlabel("n"); ylabel("h(n)");
title("h(n) (zero-padded for circular conv)");
subplot(3,1,3);
plot2d3(naxis, y);
xlabel("n"); ylabel("y(n)");
title("Circular Convolution y(n)");
```


## OUTPUT (Linear Convolution): 

<img width="1919" height="1079" alt="1" src="https://github.com/user-attachments/assets/574083c7-1dac-4f73-81be-247da81795f1" />

<img width="1918" height="1078" alt="2" src="https://github.com/user-attachments/assets/4e60def0-bbb3-4ada-92f3-4f1439f50fdb" />

## OUTPUT (Circular Convolution): 
<img width="1919" height="1079" alt="3" src="https://github.com/user-attachments/assets/a4dd88e8-c371-4df3-aa56-e5ebe9b5e7a0" />

<img width="1918" height="1078" alt="4" src="https://github.com/user-attachments/assets/179030e2-52d2-4978-abdb-406719836c3c" />


## RESULT: 
Linear and Circular Convolution for two given sequence is obtained using SCILAB
