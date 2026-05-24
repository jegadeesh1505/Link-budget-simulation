# Simulation of Transmitter and Receiver Gain Effects in Link Budget Calculations

## Introduction

In a wireless communication system, the transmitted signal experiences attenuation while traveling through the channel. To maintain reliable communication, antennas with suitable gains are used at both the transmitter and receiver.

A **link budget** is the calculation of all gains and losses occurring in a communication link. It helps determine the received signal power and system performance.

The major parameters involved are:

* Transmitter Power ((P_t))
* Transmitter Antenna Gain ((G_t))
* Receiver Antenna Gain ((G_r))
* Path Loss ((L_p))
* System Losses

The received power can be calculated using the Friis transmission equation:

P_r(dBm)=P_t(dBm)+G_t(dB)+G_r(dB)-L_p(dB)

Where:

* (P_r) = Received Power
* (P_t) = Transmitted Power
* (G_t) = Transmitter antenna gain
* (G_r) = Receiver antenna gain
* (L_p) = Path loss

Increasing either transmitter gain or receiver gain improves the received signal strength.

---

# MATLAB Program

```matlab
% Simulation of Transmitter and Receiver Gain Effects
% in Link Budget Calculations

clc;
clear;
close all;

% Parameters
Pt = 20;              % Transmit Power in dBm
Lp = 100;             % Path Loss in dB

% Gain ranges
Gt = 0:2:20;          % Transmitter Gain in dB
Gr = 0:2:20;          % Receiver Gain in dB

% Initialize matrix
Pr = zeros(length(Gt), length(Gr));

% Calculate received power
for i = 1:length(Gt)
    for j = 1:length(Gr)

        % Link Budget Equation
        Pr(i,j) = Pt + Gt(i) + Gr(j) - Lp;

    end
end

% Display received power matrix
disp('Received Power Matrix (dBm):');
disp(Pr);

% Plot results
figure;

surf(Gr, Gt, Pr);

xlabel('Receiver Gain Gr (dB)');
ylabel('Transmitter Gain Gt (dB)');
zlabel('Received Power Pr (dBm)');

title('Effect of Transmitter and Receiver Gain on Link Budget');

grid on;
colorbar;
```

---

# Explanation of the Program

1. The transmit power is fixed at 20 dBm.
2. Path loss is assumed to be 100 dB.
3. Transmitter gain and receiver gain are varied from 0 dB to 20 dB.
4. The received power is calculated using the link budget equation.
5. A 3D surface plot is generated to observe how antenna gains affect received power.

---

# Expected Output

* A matrix containing received power values.
* A 3D surface graph showing:

  * Increasing transmitter gain increases received power.
  * Increasing receiver gain also increases received power.
  * Maximum received power occurs when both gains are highest.

---

# Conclusion

This simulation demonstrates the importance of transmitter and receiver antenna gains in wireless communication systems. Higher antenna gains improve received signal strength and help compensate for path loss, thereby enhancing communication reliability and coverage.
