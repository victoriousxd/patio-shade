# Patio Shade Planner

An interactive tool to calculate the optimal sail size and shade coverage for your patio.

## Live Site

**[https://victoriousxd.github.io/patio-shade](https://victoriousxd.github.io/patio-shade)**

## Features

- Real-time sail length and angle calculations
- Solar position tracking (altitude and azimuth)
- Visual cross-section showing shade coverage
- Covered patio visualization with shadow projection
- Adjustable structure parameters (pole height, floor width, wall height, etc.)
- Location-based sun position (latitude/longitude)
- Date and time controls

## Usage

1. Adjust your patio structure parameters in the left panel
2. Set your location (latitude/longitude)
3. Choose a date and time
4. View the calculated sail length, angle, and coverage percentage
5. The canvas visualization updates in real-time showing the shade projection

## How It Works

The app calculates:
- **Sail Length (S_L)** — Required sail size: `√(M_H² + M_W²)`
- **Sail Angle (S_θ)** — Angle from horizontal: `cos⁻¹(M_H / S_L)`
- **Coverage** — Percentage of patio shaded based on sun position

The sun position is calculated using [SunCalc](https://github.com/mourner/suncalc).

## Stack

- Vanilla HTML/CSS/JavaScript (no framework)
- SunCalc library for solar calculations
- Canvas 2D for visualization

## Measurements

All measurements are in inches. Default patio dimensions:
- Floor width: 84"
- Wall height: 109"
