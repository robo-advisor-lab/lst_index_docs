---
description: LST Index Summary
---

# Liquid Staking Token (LST) Index

Website: [https://1b2d-190-219-102-166.ngrok-free.app/](https://1b2d-190-219-102-166.ngrok-free.app/)

Github: [https://github.com/robo-advisor-lab/staked\_eth\_optimizer](https://github.com/robo-advisor-lab/staked\_eth\_optimizer)

StarkHack Submission: [https://ethglobal.com/showcase/lst-optimizer-5pudw](https://ethglobal.com/showcase/lst-optimizer-5pudw)

### Project Description

This project aims to create a machine learning managed index of Liquid Staked Tokens (LSTs) on the Starknet Sepolia testnet. The main objective is to optimize the portfolio composition using reinforcement learning and forecasting to achieve the best possible returns. The project includes various components, such as a Flask-based web application, a reinforcement learning environment, data fetching and processing scripts, and integration with blockchain smart contracts for rebalancing the portfolio.

#### Environment Setup:

The environment is set up to simulate the trading of Liquid Staked Tokens (LSTs) with historical price data. The StakedETHEnv class extends the gym.Env class from OpenAI's Gym to create a custom Reinforcement Learning (RL) environment. This environment handles the portfolio's state, actions, rewards, and transition dynamics. Data Handling:

Historical price data is fetched using the YFinance API and processed using Pandas. The data is then used to calculate historical returns, which are necessary for training the RL agent. Additionally, the fetch\_and\_process\_tbill\_data function fetches risk-free rates from an external API, which are used to calculate metrics like the expected return.&#x20;

#### Reinforcement Learning:

The PPO (Proximal Policy Optimization) algorithm from Stable Baselines3 is used to train the RL agent. The agent interacts with the custom environment to learn an optimal policy for rebalancing the portfolio based on historical and forecasted data. During each episode, the environment simulates the portfolio's performance over a specified time period, considering both historical price changes and forecasted price movements.&#x20;

#### Forecasting:

The Prophet library is used to generate time series forecasts for each asset. These forecasts are used as part of the observation space for the RL agent, helping it make informed decisions about future portfolio compositions.&#x20;

#### Blockchain Integration:

The project integrates with the Starknet Sepolia blockchain to manage real token balances. It uses the Starknet Python SDK to interact with smart contracts, including checking balances and executing token transfers for rebalancing. Two main smart contract functions are involved: transfer\_tokens\_to\_fund and transfer\_tokens\_from\_fund, which handle the actual movement of tokens based on the RL agent's decisions.&#x20;

Test net erc20 tokens representing wstETH, rETH, and sfrxETH were deployed using [Scaffold-Stark-2](https://github.com/Quantum3-Labs/scaffold-stark-2).&#x20;

Flask API:

The Flask application provides endpoints for triggering rebalances and fetching the latest data. It also includes background tasks managed by APScheduler to ensure periodic updates and rebalances. The Flask app interacts with the RL environment, fetches the necessary data, and uses the Starknet SDK to execute the rebalances.&#x20;

Visualization:

The results of the RL agent's actions, including portfolio compositions, rewards, and normalized comparisons, are visualized using Plotly. The visualizations are embedded in both the Flask app and the Streamlit interface, providing an interactive and user-friendly way to analyze the model's performance.&#x20;

Deployment and Testing:

The application is designed to be deployed locally using ngrok for exposing the Flask server. This setup allows for easy testing and development. The project also includes error handling and logging to ensure smooth operation and facilitate debugging.

### How it's Made

Stable Baselines3 (PPO Algorithm):

Purpose: Used for implementing the reinforcement learning (RL) agent that optimizes the portfolio. Integration: The RL model interacts with the custom environment to learn and make decisions based on historical and forecasted data.&#x20;

Flask:

Purpose: Provides the web framework for the API endpoints and the main interface for interaction. Integration: Handles HTTP requests for initiating rebalances and fetching the latest data. It also serves the web pages for visualization.&#x20;

Plotly:

Purpose: For data visualization. Integration: Generates interactive graphs to visualize portfolio compositions, rewards, and normalized comparisons.&#x20;

Pandas and NumPy:

Purpose: Data manipulation and analysis. Integration: Processes historical price data, calculates returns, and handles various data transformations required for the RL environment.&#x20;

Asyncio and Aiohttp:

Purpose: Handles asynchronous operations, especially for making non-blocking HTTP requests. Integration: Ensures smooth and efficient data fetching and interactions with external services without blocking the main application.&#x20;

Starknet Python SDK:

Purpose: Interacts with the Starknet blockchain. Integration: Manages smart contract interactions, including transferring tokens and checking balances.&#x20;

Pyngrok:

Purpose: Exposes the local Flask server to the internet. Integration: Allows external access to the locally hosted Flask application, which is useful for development and testing purposes.&#x20;

YFinance and Flipside:

Purpose: Fetches historical and real-time financial data. Integration: Provides the necessary financial data inputs for model training and evaluation.&#x20;

Prophet:

Purpose: Time series forecasting. Integration: Generates forecasted prices for assets, which are used by the RL agent for decision-making.&#x20;





###
