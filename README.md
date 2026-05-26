# MMxLR
BlueDot Technical AI Safety research project - Activation Patching
# Mechanistic Interpretability: Activation Patching for Truthfulness
*Bluedot Technical AI Safety Project*

## Overview
This project investigates the internal representations of 'truth' within LLMs (specifically Qwen-2.5-1.5B) using **Activation Patching** and **Linear Probing**. Based on the methodology from the 'Geometry of Truth' research, I compare Mass-Mean (MM) and Logistic Regression (LR) probes to identify causal directions that govern model honesty.

## Key Findings
- **Causality vs. Accuracy**: While LR probes achieved higher classification accuracy (near 100%), MM probes demonstrated a stronger **Natural Indirect Effect (NIE)**, suggesting they capture a more fundamental causal lever.
- **The Steering Layer**: Identified Layer 20 as the optimal intervention point for steering model behavior, regardless of where classification accuracy peaked.
- **Honesty Steering**: Successfully modulated model responses to harmful prompts by 'nudging' activations along the discovered truth-direction vector.

## Methodology
1. **Activation Collection**: Extracted `resid_post` activations across all 28 layers.
2. **Probe Training**: Compared geometric (MM) and discriminative (LR) linear probes.
3. **Causal Sweep**: Performed a layer-wise intervention to calculate NIE.
4. **Model Steering**: Applied forward-hook interventions to shift model outputs in real-time.

