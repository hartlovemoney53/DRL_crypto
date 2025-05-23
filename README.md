# DRL_crypto

[Download here](https://github.com/hartlovemoney53/DRL_crypto/releases)

**A deep reinforcement learning research platform for crypto trading.**

`DRL_crypto` encapsulates a deep reinforcement learning engine built on top of Stable Baselines3 (SB3) and gymnasium, as well as a backtesting engine for strategy validation. 

## Features

- **Deep Reinforcement Learning Engine**:
  - Built-in support for various RL algorithms via SB3 and gymnasium.
  - Provides simplified interfaces, making it easier to apply different RL algorithms in custom environments.

- **Backtest Engine**:
  - The integrated backtest module allows users to convert agent actions into limit, IOC, FOK, or market orders to be executed by the engine. At the same time, it updates the global account status.
  - The account status simulates information from centralized exchanges (CEX), including opening timestamps, position value, and position mode (either one-way mode or double-sided mode).
  - It also supports different margin modes, such as isolated or cross-margin between various tokens, making the training of agents more realistic (though it increases complexity).

- **Algo Environment**:
  - By default, it using dictionary space by SB3, consisting of three types: `pub_price` for quick reward updates and risk control actions. `features`, which can be multi-dimensional and optionally rolling. `account_status` now is typically one-dimensional.
  - **Data Preprocessing**:
    - Provides a built-in data processing module that supports reading common market data from dataframes, such as LOB (limit order book) and trade data, with plans to integrate local order books using incremental LOB information in the future updates.
    - When processing features for observations, users are expected to input their own high-quality factors. Simple high-frequency factors and the price_percent_change sampling method are provided by default.
  - **Live Trading**:
    - For strategies with low concurrency, the custom environment can be seamlessly adapted for live trading. All data is sourced in real-time from various raw data streams, whether for training, backtesting, or live trading. While this enables real-time integration, there may be a performance trade-off in data handling during live trading.
    - In live trading mode, raw data is replaced with live market data, and actions generated by the agent are sent to the exchange instead of the backtest engine. Additionally, the account status is synchronized with real-time information from the exchange to maintain accuracy in portfolio management and decision-making.

- **Customizable Observations**:
  - Account information can be integrated into the environment's observation space as part of the state, helping the model gain a deeper understanding of both account status and market dynamics.

## Data Normalization

Includes a default normalization method that applies rolling-window scaled sigmoid normalization, ensuring that different types of data can effectively participate in the reinforcement learning process.

## Getting Started

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Lqz13Th/DRL_crypto.git
