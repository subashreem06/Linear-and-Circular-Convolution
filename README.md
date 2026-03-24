## EXP 2 : LINEAR AND CIRCULAR CONVOLUTION FOR GIVEN TWO SEQUENCE

### AIM  
 To perform Linear and Circular Convolution for two given sequence using SCILAB. 

### APPARATUS REQUIRED  
PC installed with SCILAB.   

### PROGRAM - LINEAR CONVOLUTION 
```python
clc;
clear;
x = input("First sequence x(n): ");
h = input("Second sequence h(n): ");
lx = length(x);
lh = length(h);
ly = lx + lh - 1;

y_lin_formula = zeros(1, ly);
for n = 1:ly
    for k = 1:lx
        if (n-k+1 >= 1) & (n-k+1 <= lh) then
            y_lin_formula(n) = y_lin_formula(n) + x(k)*h(n-k+1);
        end
    end
end

disp("Linear Convolution using Formula:");
disp(y_lin_formula);

y_lin_builtin = convol(x, h);
disp("Linear Convolution using Built-in Function:");
disp(y_lin_builtin);

clf;

subplot(4,1,1);
plot2d3(0:lx-1, x);
title("Input Sequence x(n)");
xlabel("n");ylabel("Amplitude");

subplot(4,1,2);
plot2d3(0:lh-1, h);
title("Input Sequence h(n)");
xlabel("n");ylabel("Amplitude");

subplot(4,1,3);
plot2d3(0:ly-1, y_lin_formula);
title("Linear Convolution - Formula");
xlabel("n");ylabel("Amplitude");

subplot(4,1,4);
plot2d3(0:ly-1, y_lin_builtin);
title("Linear Convolution - Built-in");
xlabel("n");ylabel("Amplitude");

```

### PROGRAM - CIRCULAR CONVOLUTION 
```python
clc;
clear;
x = input("Enter first sequence x(n): ");
h = input("Enter second sequence h(n): ");
lx = length(x);
lh = length(h);
N  = max(lx, lh);

x = [x zeros(1, N-lx)];
h = [h zeros(1, N-lh)];

y_circ_formula = zeros(1, N);
for n = 1:N
    for k = 1:N
        idx = pmodulo(n-k, N) +1;  
        y_circ_formula(n) = y_circ_formula(n) + x(k)*h(idx);
    end
end

disp("Circular Convolution using Formula:");
disp(y_circ_formula);

y_circ_builtin = real(ifft(fft(x).*fft(h)));
disp("Circular Convolution using Built-in FFT:");
disp(y_circ_builtin);

clf;
n = 0:N-1;

subplot(4,1,1);
plot2d3(n, x);
title("Input Sequence x(n)");
xlabel("n");ylabel("Amplitude");

subplot(4,1,2);
plot2d3(n, h);
title("Input Sequence h(n)");
xlabel("n");ylabel("Amplitude");

subplot(4,1,3);
plot2d3(n, y_circ_formula);
title("Circular Convolution - Formula");
xlabel("n");ylabel("Amplitude");

subplot(4,1,4);
plot2d3(n, y_circ_builtin);
title("Circular Convolution - Built-in FFT");
xlabel("n");ylabel("Amplitude");

```

### OUTPUT - LINEAR CONVOLUTION
<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/0138e663-05df-4f65-aec6-0f5758643e56" />
<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/9adc8c69-7d29-4269-a970-fcef0f379b90" />

### OUTPUT - CIRCULAR CONVOLUTION
<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/7d31c156-fe4c-4b4b-ba1e-5bab29715f1c" />
<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/3c22c204-1934-4a5b-87ff-cc5c8e22d05a" />


### RESULT
Thus, the linear convolution and circular convolution of two given sequences were performed and those result were verified.
