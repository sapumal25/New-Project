## Green Commuter: Carbon-Aware Route Planner 🌍

Final project for the Building AI course

## Summary

Green Commuter is a mobile application feature that uses AI to analyze real-time public transit data and energy grid carbon intensity to recommend the **lowest-carbon route** for daily commuting. The goal is to empower individuals to reduce their carbon footprint one trip at a time.

## Background

The problem Green Commuter solves is the **lack of transparency** regarding the environmental impact of public transit. While often better than driving, the carbon footprint of an electric train or tram still varies significantly based on the **real-time energy source** (e.g., wind vs. coal) powering the grid at that moment. This is a daily, frequent problem for millions of urban commuters who want to make greener choices.

My personal motivation is driven by the belief that small, frequent actions, when scaled up, can have a major climate impact. Making the 'green' choice the 'easy' choice is key. This topic is important because it connects individual behavior to complex energy grid dynamics, making the abstract concept of carbon emissions tangible.

## How is it used?

The solution is used by urban commuters via a **mobile application** similar to existing route planners.

![image of co2](/IMG_4390.jpeg)
**The process:**
1.  **User Input:** The user enters their start and end points and desired arrival time.
2.  **Route Calculation:** The system calculates multiple public transit routes (bus, train, subway).
3.  **Carbon Scoring (AI-driven):** For each segment of each route, the system queries a real-time carbon intensity model (see below) to predict the $\text{gCO}_2/\text{km}$ at the time of travel.
4.  **Recommendation:** The app displays the fastest route, the lowest-carbon route, and a "Balanced" route, visualizing the **estimated $\text{CO}_2$ emissions** for each choice.

The primary users are **environmentally conscious commuters** who already use public transport. A key need is speed and accuracy—the carbon calculation must be instantaneous to be useful.

## Data sources and AI methods

The project depends on two main data sources:

1.  **Public Transit Data:** Real-time location data, schedules, and vehicle type/capacity information (often available via city or transit authority APIs).
2.  **Energy Grid Data:** Real-time and historical data on the energy mix (gas, solar, wind, nuclear, etc.) feeding the local power grid (sources like [Electricity Maps API](https://www.electricitymap.org/)).

**AI Techniques:**

* **Regression (Time Series Forecasting):** A **Recurrent Neural Network (RNN)** or **Long Short-Term Memory (LSTM)** model would be used to forecast the **Carbon Intensity** ($\text{gCO}_2/\text{kWh}$) of the energy grid for the specific future time of the commute. This is essential because the carbon intensity changes minute-by-minute.
* **Graph/Pathfinding Algorithms:** Standard algorithms (like Dijkstra's or A\*) are used to find the fastest routes, but the AI's carbon score acts as an **additional weighted cost function** to find the *lowest-carbon* path.

## Challenges

**What the project does not solve:**

* It does **not** solve the structural problem of a high-carbon energy grid; it only helps users navigate it optimally.
* It does **not** account for individual passenger density on a vehicle, which would require high-granularity, private data and is beyond the initial scope.
* The system is highly dependent on the **accuracy of the energy grid forecasting model**.

**Ethical Considerations:**
* **Fairness:** The recommendations could inadvertently steer users towards longer or less convenient routes. Transparency about the trade-offs (e.g., "10 minutes slower, 50% less carbon") is crucial.
* **Data Privacy:** Only publicly available transit and grid data are used, minimizing privacy concerns.

## What next?

The project could grow into a platform used by city planners.
1.  **Traffic Optimization:** The AI could be adapted to model the *total* carbon impact of various city-wide traffic changes (e.g., adding a new bus lane).
2.  **Gamification and Rewards:** Integrate with local businesses to offer discounts or rewards to users who consistently choose the lowest-carbon route.
3.  **Expansion to Shipping:** Apply the forecasting model to large-scale logistics and commercial shipping routes to minimize supply chain emissions.

## Acknowledgments

* **Inspiration:** The concept is inspired by the work of carbon-aware computing initiatives and real-time grid data visualization platforms.
* **Data Source Inspiration:** [Electricity Maps](https://www.electricitymap.org/) for real-time carbon intensity data.
* **Code Inspiration:** Standard Python libraries for time series (e.g., Keras/TensorFlow for the LSTM model) and graph theory (e.g., NetworkX for route finding).
