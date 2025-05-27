---
title: "Hyperparameter Tuning with Optuna: What I Learned"
date: 2025-05-27
layout: single
tags:
  - machine learning

excerpt: "I used Optuna to tune hyperparameters across XGBoost, LightGBM, and CatBoost — and found out why tuning matters more than the model itself."
---

## Introduction

Today I focused on improving my ML models through **automated hyperparameter tuning** using **Optuna**.  
I tested three models — XGBoost, LightGBM, and CatBoost — and found that proper tuning often matters more than which model I use.

---

## What I Did

- Defined search spaces for key hyperparameters like `n_estimators`, `max_depth`, `learning_rate`, and `subsample`.
- Faced a `ValueError: nan is not acceptable`, which led me to carefully check parameter ranges and input formats.
- Completed trials and selected the best-performing settings for each model using cross-validation.

---

## What I Learned

- **LightGBM** doesn’t always perform better out of the box — tuning makes a bigger difference than I expected.
- It’s not just about RMSE. I started comparing models using SMAPE and RMSLE to capture performance more robustly.
- **Pseudo-stacking**, a form of ensemble that blends out-of-fold predictions, gave the best results in my experiments.

---

## Next Steps

- Consider including other meta-models in stacking.
- Try visualizing the performance landscape from Optuna trials.
- Write a utility for saving and reusing the best trial parameters.
