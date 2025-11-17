# EXP 2 : Linear and Circular Convolution

## AIM: 

 To perform Linear and Circular Convolution for two given sequence using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (Linear Convolution): 
```
clc;  
clear; 
x = [1 1 2 1]; 
 
h = [1 2 3 4]; 
 
m = length(x);
n = length(h);
a=0:1:m-1; 
b=0:1:n-1; 
 
subplot(3,1,1);  
plot2d3(a,x); 
xlabel('Time');
ylabel('Amplitude'); 
title('Graphical Representation of Input Signal X');

subplot(3,1,2); 
plot2d3(b,h);  
xlabel('Time'); 
ylabel('Amplitude');  
title('Graphical Representation of Impulse Signal h');
for i = 1: n+m-1 
conv_sum = 0; 
 
for j = 1:i 
 
if (((i-j+1) <= n)&(j <=m)) 
 
conv_sum = conv_sum + x(j)*h(i-j+1); 
 
end; 
 
y(i) = conv_sum; 
 
end;
 
end; 
disp(y,'Convolution Sum using Direct Formula Method = ')
subplot(3,1,3); 
plot2d3(y)  
title('Graphical Representation of output Signal y'); 
```

## PROGRAM (Circular Convolution): 

```
clc;
clear;

// Input sequences
x = [1 2 2 1];
h = [1 2 3 1];

// Length for circular convolution (take max length)
N = max(length(x), length(h));

// Zero padding if needed
x = [x, zeros(1, N-length(x))];
h = [h, zeros(1, N-length(h))];

disp("Zero-padded input:");
disp(x);
disp("Zero-padded impulse:");
disp(h);

// ---- Circular convolution using modulo ----
y = zeros(1, N);

for n = 1:N
    for k = 1:N
        j = pmodulo(n-k, N) + 1;   // pmodulo avoids negative indices
        y(n) = y(n) + x(k) * h(j);
    end
end

disp("Circular convolution result:");
disp(y);

// ---- Plot results ----
subplot(3,1,1);
plot2d3(0:N-1, x);
title("Input sequence x[n]");
xlabel("n"); ylabel("Amplitude");

subplot(3,1,2);
plot2d3(0:N-1, h);
title("Impulse response h[n]");
xlabel("n"); ylabel("Amplitude");

subplot(3,1,3);
plot2d3(0:N-1, y);
title("Circular Convolution y[n]");
xlabel("n"); ylabel("Amplitude");
```

## OUTPUT (Linear Convolution): 
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/d362b5f7-e3ad-495d-bda6-7517a12d16fc" />
<img width="1280" height="719" alt="image" src="https://github.com/user-attachments/assets/1b3db92a-9fb4-4a9f-a894-cd6868f92f1e" />



## OUTPUT (Circular Convolution): 
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/af752de5-1630-4031-96ae-d95980c1de1e" />
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/aa56d548-6d66-4bb5-a99e-e066b02bb56c" />



## RESULT: 
Linear and Circular Convolution are successfully executed in scilab
