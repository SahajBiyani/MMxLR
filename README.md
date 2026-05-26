# Mechanistic Interpretability: Activation Patching for Truthfulness
MMxLR - Mass-Mean (MM) vs Logistic Regression (LR)

BlueDot Technical AI Safety research project - Activation Patching

## Overview
This project investigates the internal representations of 'truth' within LLMs (specifically Qwen-2.5-1.5B) using **Activation Patching** and **Linear Probing**. Based on the methodology from the 'Geometry of Truth' research, I compare Mass-Mean (MM) and Logistic Regression (LR) probes to identify causal directions that govern model honesty.

Explored the mechanisms in Detecting High-Stakes Interactions with Activation Probes through internal activation patching and causal intervention analysis on the Qwen-2.5 1.5B Instruct model.

## Main Findings:
- Causal Levers vs. Correlations: While Logistic Regression (LR) probes achieved near 100% classification accuracy as early as Layer 1, causal intervention (Natural Indirect Effect) peaked in middle-to-late layers (Layer 20). This confirms that 'truth' representations are refined and utilized much later than they are first detectable.
- Mass-Mean (MM) Superiority: Supporting the 'Geometry of Truth' hypothesis, Mass-Mean probes demonstrated a stronger causal influence (|NIE|) on model output compared to LR probes, despite slightly lower classification accuracy.
- Successful Steering: Successfully steered model behavior by 'nudging' activations along the truth direction. Subtracting the truth vector at Layer 20 induced safe refusals in high-stakes destructive prompts (e.g., system deletion), while adding it maintained or increased compliance.
- Direction Alignment: Observed a high cosine similarity (~0.8) between descriptive (MM) and predictive (LR) directions in later layers, suggesting a convergence of internal reasoning mechanisms.

## Repository Structure:
- activation_patching_investigation.ipynb — Primary notebook for activation extraction, probe training, and causal layer sweeps.
- outputs/ — JSON results containing layer-wise accuracy, NIE metrics, and cosine similarities.
- steering/ — Logged outputs from model intervention experiments.

## Key Comparisons
- **Causality vs. Accuracy**: While LR probes achieved higher classification accuracy (near 100%), MM probes demonstrated a stronger **Natural Indirect Effect (NIE)**, suggesting they capture a more fundamental causal lever.
- **The Steering Layer**: Identified Layer 20 as the optimal intervention point for steering model behavior, regardless of where classification accuracy peaked.
- **Honesty Steering**: Successfully modulated model responses to harmful prompts by 'nudging' activations along the discovered truth-direction vector.

## Methodology
1. **Activation Collection**: Extracted `resid_post` activations across all 28 layers.
2. **Probe Training**: Compared geometric (MM) and discriminative (LR) linear probes.
3. **Causal Sweep**: Performed a layer-wise intervention to calculate NIE.
4. **Model Steering**: Applied forward-hook interventions to shift model outputs in real-time.

<img width="1640" height="1289" alt="image" src="https://github.com/user-attachments/assets/46a834b5-7fc8-40a3-8c61-582c3a6cb65b" />
<img width="1784" height="1184" alt="image" src="https://github.com/user-attachments/assets/d26071db-c670-43f6-b71a-6c1f15df0e92" />
<img width="1023" height="556" alt="image" src="https://github.com/user-attachments/assets/bbae5f9c-28b2-4578-ad6c-a891b0b47ef8" />
