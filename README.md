# Simulation of Transmitter and Receiver Gain Effects in Link Budget Calculations

## Introduction

In a wireless communication system, the transmitted signal experiences attenuation while traveling through the channel. To maintain reliable communication, antennas with suitable gains are used at both the transmitter and receiver.

A **link budget** is the calculation of all gains and losses occurring in a communication link. It helps determine the received signal power and system performance.

The major parameters involved are:

## Parameters in Link Budget Calculation

- Transmitter Power $(P_t)$
- Transmitter Antenna Gain $(G_t)$
- Receiver Antenna Gain $(G_r)$
- Path Loss $(L_p)$
- System Losses

The received power can be calculated using the Friis transmission equation:

$$
P_r(dBm) = P_t(dBm) + G_t(dB) + G_r(dB) - L_p(dB)
$$

Where:

- $P_r$ = Received Power
- $P_t$ = Transmitted Power
- $G_t$ = Transmitter antenna gain
- $G_r$ = Receiver antenna gain
- $L_p$ = Path loss

Increasing either transmitter gain or receiver gain improves the received signal strength.

---

## MATLAB Program

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

## Explanation of the Program

1. The transmit power is fixed at 20 dBm.
2. Path loss is assumed to be 100 dB.
3. Transmitter gain and receiver gain are varied from 0 dB to 20 dB.
4. The received power is calculated using the link budget equation.
5. A 3D surface plot is generated to observe how antenna gains affect received power.

---

## Output
## Received Power Matrix (dBm)

```text
[[-80 -78 -76 -74 -72 -70 -68 -66 -64 -62 -60]
 [-78 -76 -74 -72 -70 -68 -66 -64 -62 -60 -58]
 [-76 -74 -72 -70 -68 -66 -64 -62 -60 -58 -56]
 [-74 -72 -70 -68 -66 -64 -62 -60 -58 -56 -54]
 [-72 -70 -68 -66 -64 -62 -60 -58 -56 -54 -52]
 [-70 -68 -66 -64 -62 -60 -58 -56 -54 -52 -50]
 [-68 -66 -64 -62 -60 -58 -56 -54 -52 -50 -48]
 [-66 -64 -62 -60 -58 -56 -54 -52 -50 -48 -46]
 [-64 -62 -60 -58 -56 -54 -52 -50 -48 -46 -44]
 [-62 -60 -58 -56 -54 -52 -50 -48 -46 -44 -42]
 [-60 -58 -56 -54 -52 -50 -48 -46 -44 -42 -40]]
```
<img width="434" height="362" alt="image" src="https://github.com/user-attachments/assets/07580dcb-0132-4255-81a4-720e51a30ede" />

## Advantages
* Improves received signal strength
* Enhances communication range
* Reduces signal attenuation effects
* Increases link reliability
* Helps overcome path loss in wireless channels

## Applications
* Cellular communication systems
* Satellite communication
* Wi-Fi and WLAN networks
* Radar systems
* V2X and vehicular communication

