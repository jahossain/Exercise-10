Results
•	Frequency Response
1	Both filters behave like low-pass filters (they smooth signals).
2	The 5-point filter allows more high-frequency content.
3	The 9-point filter blocks more high frequencies → stronger smoothing.
•	Pole-Zero Plots
1	Zeros lie on the unit circle.
2	Poles are at the origin.
3	More zeros = sharper filtering.

FIR vs IIR Filters
FIR (Finite Impulse Response)
•	Impulse response ends after a short time.
•	Always stable.
•	Can have linear phase (no signal distortion).
•	Example: Moving Average Filter.
IIR (Infinite Impulse Response)
•	Impulse response continues forever (because of feedback).
•	Can be unstable if not designed carefully.
•	More efficient (needs fewer coefficients).
•	Examples: Butterworth, Chebyshev filters.




# Exercise-10
% Exercise 10 - Moving Average Filter

% Coefficients
b1 = [1 1 1 1 1];  % 5-point moving average
a1 = 1;

b2 = [1 1 1 1 1 1 1 1 1];  % 9-point moving average
a2 = 1;

% Frequency response of 5-point filter
[H1, w1] = freqz(b1, a1, 512);
figure;
subplot(2,2,1);
plot(w1/pi, abs(H1));
title('TransferFunction of 5 point MAF');
xlabel('Normalized Frequency (\times\pi rad/sample)');
ylabel('|H1|');

% Pole-zero plot of 5-point filter
subplot(2,2,2);
zplane(b1, a1);
title('Pole-zero plot of 5 point MAF');

% Frequency response of 9-point filter
[H2, w2] = freqz(b2, a2, 512);
subplot(2,2,3);
plot(w2/pi, abs(H2));
title('TransferFunction of 9 point MAF');
xlabel('Normalized Frequency (\times\pi rad/sample)');
ylabel('|H2|');

% Pole-zero plot of 9-point filter
subplot(2,2,4);
zplane(b2, a2);
title('Pole-zero plot of 9 point MAF');

% Transfer function to zero-pole-gain conversion
[z1, p1, k1] = tf2zp(b1, a1);
[z2, p2, k2] = tf2zp(b2, a2);

disp('Zeros, Poles, and Gain of 5-point MAF:');
disp(z1); disp(p1); disp(k1);

disp('Zeros, Poles, and Gain of 9-point MAF:');
disp(z2); disp(p2); disp(k2);
