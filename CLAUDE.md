# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project directory

`patio-shade/index.html` — single self-contained file, no build step.

## Stack

- Vanilla HTML/CSS/JS, no framework
- [SunCalc](https://github.com/mourner/suncalc) via CDN for solar position (altitude, azimuth)
- Canvas 2D for the cross-section visualization

## Hosting

Static file → deploy free to Netlify (drag-and-drop the folder) or GitHub Pages.

## Project

Patio shade planner — an interactive app where the user inputs physical measurements of their patio structure, and the app calculates the required sail size and angle to achieve coverage.

## Domain: Sail Size & Angle Calculator

All measurements in inches.

**Variables (user-adjustable):**
- `P_H` — pole height
- `F_W` — floor width
- `W_H` — wall height
- `G_L` — length between wall and grate mount

**Known constants (this specific patio):**
- `F_W = 84`
- `W_H = 109`

**Intermediate values:**
- `M_H = W_H - P_H`
- `M_W = F_W - G_L`

**Outputs:**
- `S_L = √(M_H² + M_W²)` — required sail length; subtract 10–12 in for hardware/harness
- `S_θ = cos⁻¹(M_H / S_L)` — sail angle from horizontal

## Domain: Shade Coverage Model

**Additional variables:**
- `L_θ` — angle the sun hits the patio; changes throughout the day and by season (computed via pvlib)
- `D_H` — shadow height cast by the sail
- `D_A` — area of shade on the patio

**Solar position tool:** pvlib — used to derive `L_θ` (solar zenith/azimuth) over time.

**Sun behavior — two phases per day:**
1. High sun: ~1:00–4:15 PM
2. Low sun: 4:15 PM → sunset (sun angle is low, shade geometry changes significantly)

**Seasonal coverage targets:**
- Early summer: 100% patio coverage holds until ~4:00 PM
- Late summer: 100% coverage holds until ~3:00 PM

**Design levers:**
- Lower `P_H` → increases `D_A`
- Minimize `S_θ` → steeper sail → different shadow geometry
- Vertical drop attachment option affects shade shape
