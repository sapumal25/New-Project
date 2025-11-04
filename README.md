# Green Commuter: Carbon-Aware Route Planner 🌍

Final project for the Building AI course

## Summary

Green Commuter is a mobile application feature that uses AI to analyze real-time public transit data and energy grid carbon intensity to recommend the **lowest-carbon route** for daily commuting. The goal is to empower individuals to reduce their carbon footprint one trip at a time.

## Background

The problem Green Commuter solves is the **lack of transparency** regarding the environmental impact of public transit. While often better than driving, the carbon footprint of an electric train or tram still varies significantly based on the **real-time energy source** powering the grid. This project helps commuters make greener choices every day.

My personal motivation comes from the belief that small, frequent actions can have a major climate impact. Making the 'green' choice the 'easy' choice is key.

## How It Works

Urban commuters use the solution via a **mobile application** similar to existing route planners.

**Process:**
1. **User Input:** Enter start/end points and desired arrival time.
2. **Route Calculation:** System calculates multiple public transit routes (bus, train, subway).
3. **Carbon Scoring (AI-driven):** For each segment, the system predicts the $\text{gCO}_2/\text{km}$ using a real-time carbon intensity model.
4. **Recommendation:** App displays fastest, lowest-carbon, and "Balanced" routes with estimated $\text{CO}_2$ emissions.

**Primary Users:** Environmentally conscious commuters who prioritize both speed and low-carbon choices.

## Data Sources and AI Methods

**Data Sources:**
- **Public Transit Data:** Real-time location, schedules, and vehicle info via APIs.
- **Energy Grid Data:** Real-time/historical energy mix (gas, solar, wind, nuclear) from sources like [Electricity Maps API](https://www.electricitymap.org/).

**AI Techniques:**
- **Regression/Time Series Forecasting:** RNN or LSTM models forecast **Carbon Intensity** ($\text{gCO}_2/\text{kWh}$) for future commute times.
- **Graph/Pathfinding Algorithms:** Dijkstra's or A* finds fastest routes; AI carbon scores act as additional weights for lowest-carbon paths.

## Challenges

**Limitations:**
- Does **not** solve high-carbon energy grid issues.
- Does **not** account for individual passenger density.
- Depends on the **accuracy of energy grid forecasting**.

**Ethical Considerations:**
- **Fairness:** Recommendations may prioritize carbon over speed. Trade-offs should be transparent.
- **Privacy:** Only public data is used, minimizing privacy concerns.

## Future Work

Potential expansions include:
1. **Traffic Optimization:** Model city-wide carbon impact of traffic changes.
2. **Gamification/Rewards:** Encourage low-carbon choices with incentives.
3. **Expansion to Shipping:** Apply forecasting to logistics for lower emissions.

## Acknowledgments

- Inspired by carbon-aware computing initiatives and grid visualization platforms.
- Data source inspiration: [Electricity Maps](https://www.electricitymap.org/)
- Code inspiration: Python libraries like Keras/TensorFlow (LSTM) and NetworkX (graph algorithms).
