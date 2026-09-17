# Fitts's law experiment study
An empirical Fitts's law study evaluating the screen-edge effect on target acquisition time.


This project investigates asymmetric touch target design in high-intensity mobile MOBA (Multiplayer Online Battle Arena) gaming using Fitts' Law. It empirically validates how sizing and spatial layout prevent game-losing accidental clicks during high-adrenaline combat.

- **Live Experiment Application:** [https://yu034604-crypto.github.io/fitts-law-study/](https://yu034604-crypto.github.io/fitts-law-study/)

---

## 1. Scenario, Innovation, and Application

### Scenario & Context
* **Context:** Competitive mobile MOBA games (e.g., *Arena of Valor* / *Honor of Kings*).
* **User State:** During high-stakes team fights, players experience intense physiological arousal, adrenaline rush, and extreme time pressure. Every split second determines victory or defeat. Players must repeatedly execute basic attacks (`ATTACK`) from a default resting finger position, while non-combat utility buttons (such as settings, shop, scoreboard, or chat emotes) occupy nearby interface space.

### Real-World HCI Problem
When players enter high-stress combat, adrenaline and rapid tapping cause motor tremors, visual tunnel vision, and spatial overshooting ("fat-finger" errors). In mobile MOBAs like *Arena of Valor*, accidentally tapping a non-combat button (e.g., opening the settings menu, store overlay, or chat window) instead of the attack button instantly interrupts basic attack combos, leading to disastrous in-game wipeouts and defeats.

### Innovation: Asymmetric Spatial & Target Biasing
* **Biased Target Dimensions:** The critical `ATTACK` button is made significantly larger ($W = 96\text{ px}$) and highly prominent to provide maximum error tolerance during rapid, high-frequency tapping. Conversely, non-combat utility buttons (`CONFIG` / Settings) are drastically miniaturized ($W = 28\text{ px}$).
* **Distance Stratification:** The `ATTACK` button is positioned closer to the default resting position ($A = 140\text{ px} - 210\text{ px}$), enabling rapid motor reflex execution. The non-combat button is placed farther away ($A = 280\text{ px}$) toward the peripheral corners.
* **Fitts' Law Asymmetry:** By deliberately driving up the Index of Difficulty ($ID = \log_2(2A/W)$) for non-combat buttons through smaller width and longer travel distance, the interface imposes deliberate motor friction, preventing accidental triggers without disabling functional access.

### Application & Potential Real-World Extensions
* **Current Experimental App:** A single-page interactive canvas that mimics a mobile MOBA combat station with an origin resting point, 9 randomized $A \times W$ conditions, real-time miss logging, and aggregated Mean Movement Time (MT) export.
* **Broad Real-World Applications:**
  1. **Mobile Gaming Controls (MOBA / FPS):** Differentiating primary fire/attack buttons from secondary utility buttons (reload, chat, surrender, store) to protect competitive play.
  2. **Automotive Cockpit Touchscreens:** Making emergency hazard lights and climate toggle buttons large and close to the driver's resting hand position, while making vehicle configuration menus smaller and positioned further away to prevent accidental glances or touches while driving.
  3. **Emergency Dispatch & Medical UI:** Designing primary dispatch/defibrillator triggers with low $ID$ (large, accessible) and destructive reset/abort buttons with high $ID$ (small, edge-aligned) to avoid fatal operational slips under crisis.

---

## 2. Why Choose This Design?

I chose this design directly from my personal experience playing *Arena of Valor* (*傳說對決*). During crucial team fights, intense excitement and panic tapping often lead to accidental slips onto adjacent non-combat buttons—such as settings or the chat wheel—instantly causing team wipeouts and defeats. 

Standard HCI design guidelines often assume that all on-screen elements should be equally accessible. However, high-stress interaction requires **asymmetric error resilience**: vital, time-critical actions should be biomechanically effortless, while disruptive non-combat functions must require intentional, high-precision motor movement. This experiment demonstrates how Fitts' Law can be used proactively to protect users from high-arousal motor errors.

## 3. Empirical Analysis & Custom Formula

### Video Demonstration
<!-- Embed your recorded screen trial video or insert your YouTube link below -->
(https://drive.google.com/file/d/19qEwJHRBMYSZu0J9C42Gui9THX-8oTjR/view?usp=sharing)

### Regression Scatter Plot
<img width="752" height="452" alt="image" src="https://github.com/user-attachments/assets/8a287009-de6a-4532-8a90-30df6cf64344" />


### Custom Fitts' Law Formula
Empirical regression derived from 9 randomized conditions (90 valid clicks aggregated into Mean Movement Time):

$$MT = a + b \cdot ID$$

$$MT = 57.64 + 139.21 \cdot \log_2\left(\frac{2A}{W}\right)$$

* **Intercept ($a$):** $57.64\text{ ms}$ (baseline sensory-motor initiation delay)
* **Slope ($b$):** $139.21\text{ ms/bit}$ (information processing rate)
* **Coefficient of Determination ($R^2$):** $0.8483$ (demonstrating a robust fit to Fitts' Law)
* **Throughput ($TP = 1/b$):** $\approx 7.18\text{ bits/s}$

### Empirical Discussion
The empirical findings strongly validate the asymmetric layout:
1. **Low $ID$ for Core Combat:** The large, centrally positioned `ATTACK` button yielded rapid movement times ($269.6\text{ ms} - 422.6\text{ ms}$), enabling split-second reflex engagement.
2. **High $ID$ for Protective Friction:** The miniaturized, peripheral `CONFIG` button exhibited elevated movement times ($490.1\text{ ms} - 653.8\text{ ms}$), creating a physical protective threshold against accidental triggering during intense combat scenarios.
