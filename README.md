# Bayesian-Epidemic-Modeling
## Introduction
This project explains how we can use Bayesian statistics to model disease outbreaks. We’ll use the SIR (Susceptible-Infected-Recovered) model to estimate how quickly a disease spreads (infection rate β) and how quickly people recover (recovery rate γ).
### 1. Bayesian methods help us:
- Combine prior knowledge with new data
- Quantify uncertainty in our estimates
- Make better predictions to guide public health decisions
### 2. Estimates:
- Infection rate (𝛽): How easily the disease spreads.
- Recovery rate (𝛾): How quickly infected individuals recover.
### 3. The SIR Model
The SIR model divides a population into three compartments:
* Susceptible: Can catch the disease
* Infected: Currently have and can spread the disease
* Recovered: Had the disease and are now immune
  - $$\frac{dS}{dt} = -\beta S \frac{I}{N}, \quad \frac{dI}{dt} = \beta S \frac{I}{N} - \gamma I, \quad \frac{dR}{dt} = \gamma I$$
* Bayesian inference estimates 𝛽 and 𝛾, incorporating prior knowledge:
  - $$\beta \sim \text{Beta}(2, 5), \quad \gamma \sim \text{Beta}(3, 7)$$
![image](https://github.com/user-attachments/assets/c5b1b198-49c1-4b76-9bee-e8e5c2434f21)
## Bayesian Approach
- These numbers are initial guesses (our priors) for an epidemic model: 
  * Infection rate (β) = ~29%; About 29% of exposed people get infected per day. 
  * Recovery rate (γ) = ~31%; About 31% of sick people recover per day.
- After updating with real data: 
  * Both models now estimate that the true infection rate is about 11.3% and recovery rate is about 11.9%. 
  * The credible intervals tell us we’re 95% confident that the true rate lies somewhere between roughly 6.13% and 18.29% and for recovery rate roughly 6.26% and 18.47%.
![image](https://github.com/user-attachments/assets/eaf4149f-b9aa-46db-8b7c-561b8fd39f8d)
## Metropolis-Hastings Sampling
- We will use this algorithm to estimate the posterior distributions of β and γ.
- Trace Plots show the journey of the algorithm’s guess for infection rate (β) and recovery rate (γ) over time.
![image](https://github.com/user-attachments/assets/d8655b44-a43c-46c1-86e8-05a2d6240061)
## Model Sensitivity:
•	This shows how different priors lead to different outbreak forecasts
•	Original priors (Beta(2,5), Beta(3,7)) vs more informative vs uninformative
•	Visualizes the range of possible trajectories
![image](https://github.com/user-attachments/assets/2e681b29-c20c-4679-8b5c-78677e4697f6)
## Data Limitations: Under-Reporting
•	Modifies the likelihood to account for under-reporting probability
•	Shows how parameter estimates change with different reporting rates
•	Critical for real-world applications where not all cases are detected
![image](https://github.com/user-attachments/assets/19f63b30-04a5-4242-a31f-88ef396f94c1)
## Policy Implications:
- Provides concrete policy recommendations based on:
  * Probability transmission rate exceeds critical threshold
  * Probability outbreak will grow (R0>1)
![image](https://github.com/user-attachments/assets/bd9e8d79-d5d2-47c5-85d4-407fbf4be3a5)
## Bayesian Agent-Based Model (ABM)
* Agents can be in different health states: Shielded (H) = Healthy and vulnerable; Infiltrated (I) = Infiltrated Infected but not infectious yet; Spreader (S) = Actively contagious; Resistant (R) = Recovered with immunity; Fallen (F) = Died due to infection
* Places: Homes (high risk); Schools (medium risk); Work (medium risk)️; Public (low risk)
![image](https://github.com/user-attachments/assets/ec4590a7-3bd8-4874-b3d0-d468900d10af)
* BayesianABM Network
![image](https://github.com/user-attachments/assets/00060fbb-d486-4ed1-8a49-c6db398cb3cf)
* Each Bubble = 1 person
### 1. Start (Day 1): 
- Most bubbles are lightblue (healthy) 
- A few red bubbles appear (first sick people)
### 2. Middle (Day 10-15): 
- Red bubbles spread like fire 
- You see darkred bubbles turn red (people getting sick) 
- Darkgreen bubbles start appearing (people getting better/immune)
### 3. End (Day 30): 
- More darkgreen bubbles (recovered people) 
- Fewer salmon bubbles (sickness slowing down) 
- Some black bubbles (unfortunate losses)
