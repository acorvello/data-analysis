# 🚀 Lunar Lander v3 - Deep Reinforcement Learning Benchmark

This repository presents a comprehensive engineering and modeling project in **Deep Reinforcement Learning (Deep RL)** applied to the continuous physical control of the **Lunar Lander v3** environment (Gymnasium).

The primary objective is to train and audit intelligent agents capable of reading vector telemetries from a spacecraft and firing thrusters in a coordinated manner to execute a safe landing on the lunar pad.

---

## 💡 Technical Highlights of the Pipeline

Unlike purely theoretical or academic approaches, this project was designed under software engineering and AI performance best practices:

* **100% In-Memory Architecture (RAM):** The training ecosystem has been decoupled from physical disk writes. Environments, training buffers, logs, and convergence curve history are processed and held strictly in volatile memory, keeping the development workspace clean.
* **Gradient Stabilization:** Utilization of monitored and encapsulated environments wrapped with **Adaptive Reward Normalization (`VecNormalize`)** to mitigate the noisy impact of score spikes (+100 for landing / -100 for crashing).
* **Algorithm Competition:** A simultaneous comparative evaluation among three major logical families from the `Stable-Baselines3` framework: **DQN** (value-based), **PPO** (policy gradient-based), and **A2C** (synchronous Actor-Critic architecture).
* **Auditing via Shannon Entropy:** Implementation of fine-grained mathematical diagnostics to measure the behavioral plasticity of neural networks post-training, shielding the repository against the *Policy Collapse* phenomenon (where the agent becomes blind and repeatedly issues the same command).

---

## 📊 Quantitative Results Summary (300k Steps)

Following a controlled budget of **300,000 interaction timesteps**, the models were subjected to deterministic testing under independent stochastic seeds. The **PPO** algorithm emerged as the absolute champion:

| Algorithm | Mean Reward | Standard Deviation (Stability) | Safe Landing Rate (Success) | Shannon Entropy | Policy Health Status |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 🏆 **PPO** | **+184.20** | **14.50** | **93.3%** | **1.91 bits** (Max: 2.00) | ✅ Healthy & Dynamic |
| 🥈 **A2C** | -42.10 | 38.60 | 15.0% | 1.10 bits | ⚠️ Late Degradation |
| 🥉 **DQN** | -125.40 | 45.10 | 0.0% | 0.32 bits | 🚨 Collapse Alert |

### 🧠 Engine Firing Profile (Champion PPO Model):
* **IDLE (Inertial Drifting):** 25.5%
* **LEFT_THRUSTER (Left Lateral Correction):** 17.6%
* **RIGHT_THRUSTER (Right Lateral Correction):** 17.3%
* **MAIN_THRUSTER (Vertical Braking Propulsion):** 39.7%

---

## 🛠️ Requirements and Installation

The project exclusively utilizes open-source tools (MIT License), eliminating any dependencies on proprietary ROMs or third-party commercial emulators.

1. Ensure you have Python 3.10+ installed.
2. Clone the repository and install the dependencies listed in the `requirements.txt` file:

```bash
pip install -r requirements.txt
```

### Core Components of `requirements.txt`:
* `gymnasium[box2d]` (Physical engine for continuous simulation)
* `stable-baselines3` (RL algorithms framework)
* `torch` (Tensor/Neural Network processing engine)
* `tqdm`, `pandas`, `numpy`, `matplotlib`, `pygame` (Support, logging, and rendering)

---

## 🚀 How to Run the Project

The code has been structured linearly and embedded within a single Jupyter Notebook (`lunar_lander_deep_rl.ipynb`), broken down into 7 sequential steps:

1. **Cell 1 - Setup:** Library initialization and hardware mapping.
2. **Cell 2 - The "Before":** Inline demonstration of the spacecraft crashing randomly prior to training.
3. **Cell 3 - Infrastructure:** Configuring the in-memory vector factory (RAM) and the evaluation function.
4. **Cell 4 - Training:** Asynchronous execution of DQN, PPO, and A2C managed by `tqdm` progress bars.
5. **Cell 5 - Stress Board:** Automated generation of the scientific convergence graph and Pandas ranking.
6. **Cell 6 - The "After":** Inline, stabilized visual demonstration of the champion model performing an autonomous landing.
7. **Cell 7 - Diagnostics:** Fine-grained auditing of Shannon entropy bits and predictive scalability analysis.

---

## ⚖️ License

This repository is licensed under the **MIT License**. Feel free to clone, study, modify, and distribute the code for educational or portfolio purposes.
