# Fitts's law experiment study
This project investigates asymmetric touch target design in high-intensity mobile MOBA (Multiplayer Online Battle Arena) gaming using Fitts' Law. It empirically validates how sizing and spatial layout prevent game-losing accidental clicks during high-adrenaline combat.

- **Live Experiment Application:** [https://yu034604-crypto.github.io/experiment-study/)

---

## 1. Scenario, Innovation, and Application
### Scenario & Context
* **Scenario:** Competitive mobile MOBA games (e.g., Arena of Valor).
* **User Context:** During critical team fights, players experience intense physiological excitement, adrenaline rush, and extreme time pressure. Players must repeatedly execute basic attacks (`ATTACK`) from a default resting finger position, while non-combat utility buttons (`CFG` / Settings, chat, scoreboard) share the same touch surface.

### Real-World HCI Problem
Under high stress and rapid tapping, players frequently suffer from motor slips and "fat-finger" errors. In games like *Arena of Valor*, accidentally tapping a non-combat button instead of the attack button interrupts attack combos or brings up menus, directly resulting in team wipeouts and defeats.

### Innovation: Asymmetric Target Sizing & Distance Stratification
* **Asymmetric Target Dimensions:** 
  * The critical `ATTACK` button is large ($W = 96\text{ px}$) to provide maximum error tolerance during rapid combat tapping.
  * Non-combat utility buttons (`CFG`) are downsized ($W = 28\text{ px}$ or $54\text{ px}$) to reduce their touchable surface area.
* **Distance Stratification:** 
  * Target distances from the resting position vary systematically across $A = 140\text{ px}, 210\text{ px}, 280\text{ px}$.
  * `ATTACK` targets remain within the central action zone, whereas `CFG` targets are pushed toward peripheral edges and corners.
* **Fitts' Law Mechanism:** By intentionally elevating the Index of Difficulty for `CFG` through reduced width and peripheral placement, the layout creates physical motor friction that naturally prevents accidental triggers.

### Application & Real-World Extensions
* **Current Experimental Tool:** A responsive web application featuring real-time millisecond stopwatch timing, live MT display, dynamic $A$ & $W$ parameters, 9 randomized conditions, and aggregated CSV data export.
* **Real-World Extensions:**
  1. **Mobile Gaming (MOBA / FPS):** Prioritizing primary fire buttons over sensitive reload, store, or surrender controls.
  2. **Automotive Cockpit Touchscreens:** Making primary defroster/hazard controls large and near the hand rest, while placing deep system settings far away and small to prevent distracted driving slips.
  3. **Medical & Emergency Interfaces:** Designing critical shock/inject triggers with low $ID$ and abort/reset functions with high $ID$ to eliminate fatal slips under crisis.

---

## 2. Why I Chose This Design?

I chose this design directly from my personal experience playing *Arena of Valor*. During crucial team fights, intense excitement and panic tapping often lead to accidental slips onto adjacent non-combat buttons—such as settings or the chat wheel—instantly causing team wipeouts and defeats. 

Standard HCI design guidelines often assume that all on-screen elements should be equally accessible. However, high-stress interaction requires **asymmetric error resilience**: vital, time-critical actions should be biomechanically effortless, while disruptive non-combat functions must require intentional, high-precision motor movement. This experiment demonstrates how Fitts' Law can be used proactively to protect users from high-arousal motor errors.

## 3. Empirical Analysis & Custom Formula

### Video Demonstration
<!-- Embed your recorded screen trial video or insert your YouTube link below -->
https://github.com/user-attachments/assets/0947ef0f-3856-4319-8ae2-f88e9ce392b0

### Regression Scatter Plot
<img width="500" height="350" alt="image" src="https://github.com/user-attachments/assets/eb3371ea-3117-4202-ad82-734a43f1e531" />

### Custom Fitts' Law Formula
Empirical regression derived from 9 randomized conditions (90 valid clicks aggregated into Mean Movement Time):

$$MT = 3.3808 + 166.65 \cdot \log_2\left(\frac{A}{W}+1\right)$$

* **Intercept ($a$):** $3.3808\text{ ms}$ (baseline sensory-motor initiation delay)
* **Slope ($b$):** $166.65\text{ ms/bit}$ (information processing rate)
* **Coefficient of Determination ($R^2$):** $0.9327$ (demonstrating a robust fit to Fitts' Law)
