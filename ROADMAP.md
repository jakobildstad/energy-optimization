# AI‑Driven Energy Optimization for a Mobile Robot — Roadmap

| Phase | Week | Milestones | Key Deliverables |
|-------|------|------------|------------------|
| **1. Environment Setup** | 1 | • Add PyBullet to `requirements.txt`<br>• Create `src/env/pybullet_env.py` with a simple ground‑plane + mobile‑robot URDF (e.g., TurtleBot) | Reproducible simulation that resets & steps via Gym‑style API |
| **2. Energy Modeling** | 2 | • Implement `src/utils/energy.py` with `compute_energy(action, joint_states)`<br>• Log cumulative energy per episode | Unit‑tested energy function, imitation of battery drain |
| **3. Baseline Controller** | 3 | • Scripted waypoint follower in `src/models/baseline_pid.py`<br>• Evaluate over 100 episodes, save stats to `data/baseline_metrics.csv` | 📊 Baseline energy & time metrics |
| **4. RL Agent (PPO)** | 4‑5 | • Integrate Stable‑Baselines3 PPO in `src/models/ppo_agent.py`<br>• Reward = − α · energy − β · time + γ · goal_reached | 🏋️‍♂️ Trained checkpoint & TensorBoard logs |
| **5. Hyper‑Tuning & Ablation** | 6 | • Sweep α, β, γ with Optuna<br>• Compare PPO vs SAC in `notebooks/tuning.ipynb` | 📈 Ablation plots + best hyper‑params |
| **6. Evaluation Suite** | 7 | • `src/analysis/evaluate.py` produces CSV & plots for baseline vs RL<br>• Metrics: total kJ, finish time, collisions | 📑 `docs/report.md` with tables & charts |
| **7. Visualization & Demo** | 8 | • Record PyBullet GIFs (baseline vs optimized)<br>• Live Matplotlib energy‑over‑time graph in `scripts/demo.py` | 🎥 Demo video + shareable notebook |
| **8. Packaging & Write‑up** | 9 | • Clean API, update README usage examples<br>• Publish blog/LinkedIn post and push tagged release | 🚀 Public GitHub release v0.1 |

## Optional Next Steps
- **Sim‑2‑Real:** Collect actuator current on a physical TurtleBot and fine‑tune.  
- **Multi‑Objective RL:** Add path smoothness or safety constraints.  
- **MLOps:** Dockerfile + GitHub Actions CI for tests and training workflow.
