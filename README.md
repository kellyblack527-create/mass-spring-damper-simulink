# Mass-Spring-Damper System — Simulink Simulation

A dynamic simulation of a single degree-of-freedom mass-spring-damper system built in MATLAB Simulink, driven by a sinusoidal external force.

## System Overview

The system models a mass connected to a fixed wall via a spring and damper, subjected to an external force f(t).

**Governing Equation:**

mẍ + cẋ + kx = f(t)

## Parameters

| Parameter | Value |
|-----------|-------|
| Mass (m) | 2 kg |
| Damping coefficient (c) | 2 N.s/m |
| Spring stiffness (k) | 8 N/m |
| External force f(t) | 2sin(2t) N |

## Simulink Model Structure

The model implements the equation of motion by solving for acceleration directly:

ẍ = (1/m)(f(t) − cẋ − kx)

Two integrators are used in series: the first converts acceleration to velocity, the second converts velocity to position. Velocity and position are fed back to compute the damping and spring forces respectively.

## Key Finding — Resonance

Plotting the input force and displacement response on the same scope revealed a phase shift between the two signals — the force leads, the displacement lags.

The phase angle is given by:

φ = arctan(cω / (k − mω²))

With the driving frequency ω = 2 rad/s matching the system's natural frequency ωₙ = √(k/m) = 2 rad/s exactly, the denominator goes to zero, giving φ = 90°. The system was unknowingly driven at resonance, producing the maximum possible phase shift.

## Results

- Damped oscillatory response settling toward steady state
- 90° phase shift between force input and displacement output confirmed visually via scope

## Tools

- MATLAB Simulink
