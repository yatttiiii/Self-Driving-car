
 Deep Q-Learning for Self-Driving in CARLA

Ever wondered how a car learns to drive by itself? This project is a simple but powerful implementation of a **Deep Q-Network (DQN)** agent trained to drive in the **CARLA simulator**, using only a front-facing RGB camera and some clever reinforcement learning.

The goal? Train a neural network to make driving decisions — accelerate, go straight, or turn — based on what it "sees".



 What’s Inside?

- A complete DQN pipeline built with **Keras** and **TensorFlow**
- Visual input processing using **Xception CNN**
- Custom reward system based on speed and collisions
- A live spectator camera that follows the car
- Detailed training stats via **TensorBoard**
- CARLA integration for environment simulation



 File Overview

- `afpy.py` – The main script: sets up the environment, the agent, and runs training.
- `models/` – Trained models are saved here automatically.
- `logs/` – TensorBoard logs to monitor training progress.

---

## ⚙️ Requirements

Install the Python dependencies:

```bash
pip install numpy opencv-python tensorflow keras tqdm
````

Also required:

* **CARLA Simulator** (v0.9.x recommended)
* CARLA Python API (.egg file must be in your Python path)

Make sure CARLA is running on `localhost:2000` before you start training.

 
 How to Run It

1. Start the CARLA simulator.

2. Then run the script:

```bash
python afpy.py
```

3. Want to see how the agent is learning? Open TensorBoard:

```bash
tensorboard --logdir logs/



 How the Agent Learns

* **Episodes**: 100 (modifiable)
* **Actions**: Steer Left, Straight, Steer Right
* **Rewards**:

  * ✅ +1 if driving over 50 km/h
  * 💤 -1 if too slow
  * 💥 -200 on collision
* **Exploration** (ε-greedy policy):

  * Starts at ε = 1.0 (full exploration)
  * Gradually decays to ε = 0.001 (more confident over time)


 How It Works (in short)

* `CarEnv` sets up the car and sensors inside CARLA.
* `DQNAgent` builds and trains the neural network using experience replay.
* A separate thread handles background training.
* After each episode, the agent improves by learning from its past experiences.


 Highlights

* Smooth integration with CARLA
* Uses Xception CNN for strong feature extraction
* Real-time training stats with custom TensorBoard support
* Modular code – easy to extend with new sensors or reward logic



 Author

Made with curiosity and TensorFlow.
Feel free to fork, tweak, and play around!
