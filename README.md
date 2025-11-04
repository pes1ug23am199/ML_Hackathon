# 🧠 Hackman — Intelligent Hangman Agent
### UE23CS352A: Machine Learning Hackathon

**Hackman** is an intelligent Hangman-solving agent that combines probabilistic reasoning (Hidden Markov Model) and reinforcement learning (Q-Learning) to guess words efficiently and accurately. The goal is to design an AI system that learns to play Hangman by leveraging language patterns and decision-based learning.

## 📘 Project Overview
The project builds a hybrid model:  
1. An **HMM** trained on a 50,000-word corpus to estimate letter probabilities based on the current masked pattern.  
2. A **Reinforcement Learning Agent** that uses those probabilities to make optimal guesses and minimize wrong attempts.

## 🧠 System Architecture
**Hidden Markov Model (HMM):** Trained on `corpus.txt` to learn letter dependencies and transitions. Hidden states represent unknown letters; emissions represent observed ones. The HMM outputs a probability distribution over A–Z based on the current masked pattern.  
**Reinforcement Learning Agent (Q-Learning):** Learns to make optimal guesses through interaction with a Hangman environment and integrates HMM probabilities as priors for informed decision-making.

## 🧩 State, Actions, and Rewards
**State Representation:** `(masked pattern, guessed letters, remaining lives, HMM probabilities)`  
**Actions:** 26 possible actions — guessing any unused letter from A–Z.  
**Reward Function:**
| Event | Reward |
|--------|--------|
| Correct guess | +10 |
| Wrong guess | −5 |
| Repeated guess | −2 |
| Word solved | +50 |
| Game lost | −50 |

This reward system promotes accuracy, discourages repetition, and rewards successful word completion.

## ⚙️ Exploration Strategy
An **ε-greedy** policy manages exploration vs exploitation. Training begins with **ε = 0.6** and gradually decays to **ε = 0.05** using a decay rate of **0.9995 per episode**, allowing the agent to explore more in early stages and exploit learned strategies later.

## 🧩 Implementation Components
- **BigramHMM:** Learns letter-to-letter transitions and provides posterior probabilities for next guesses.  
- **HangmanEnv:** Custom environment handling word generation, guesses, and game rules.  
- **QLearningAgent:** Learns Q-values from rewards, updates policy, and balances exploration/exploitation.  
- **Training Loop:** Simulates multiple games to train the agent.  
- **Evaluation:** Tests on unseen words using the scoring formula:  
`Final Score = (Success Rate × 2000) − (Wrong Guesses × 5) − (Repeated Guesses × 2)`

## 📊 Results and Insights
- The agent learns meaningful linguistic patterns such as prioritizing vowels.  
- HMM integration improved convergence speed and reduced random guessing.  
- Reward shaping and ε-decay produced a stable success rate of over 50% on unseen test words.  
- Visualizations show smoother reward trends and declining exploration rates over time.

## 🚀 Future Improvements
- Replace Q-table with a **Deep Q-Network (DQN)** for larger state spaces.  
- Dynamically update HMM probabilities after each guess.  
- Introduce **curriculum learning** from short-to-long words.  
- Use **n-gram** or **transformer-based models** for richer context.  
- Parallelize training for faster convergence.

## 🧭 Steps to Run
### 1️⃣ Prerequisites
Install Python 3.8+ and required libraries:
```bash
pip install numpy matplotlib
```

### 2️⃣ Prepare Data
Ensure these files are in the working directory:
```bash
corpus.txt
test.txt
```
### 3️⃣ Run the Program
Execute:
```bash
python main.py
```

### This will:
- Train the HMM on the corpus.  
- Train the Q-Learning agent for **8000 episodes**.  
- Evaluate the agent on **2000 test words**.  
- Display **training and evaluation visualizations**.

---

### 4️⃣ Outputs
- **Training progress logs**  
- **Four plots:**
  - Reward per Episode  
  - Epsilon Decay  
  - Smoothed Reward Curve  
  - Evaluation Summary  
- **Evaluation metrics:**
  - Success Rate  
  - Wrong Guesses  
  - Repeated Guesses  
  - Final Score  

---

## 📁 Project Structure
```bash
├── main.ipynb
├── corpus.txt
├── test.txt
├── Analysis_Report.pdf
├── Problem_Statement.pdf
└── README.md
└── LICENSE
```

---

## 👥 Authors
Developed as part of **UE23CS352A: Machine Learning Hackathon**  
**Project Title:** *Hackman — Hybrid HMM + RL Hangman Agent*  

- [@pes1ug23am199](https://github.com/pes1ug23am199)  
- [@pes1ug23am221](https://github.com/pes1ug23am221)  
- [@pes1ug23am232](https://github.com/pes1ug23am232)  
- [@pes1ug23am203](https://github.com/pes1ug23am203)

---

## 🏁 Acknowledgements
- Department of Computer Science and Engineering(AI & ML)  
