# Battery State-of-Charge Estimation with a BiLSTM

## What this project is about

**How much charge is left in a lithium-ion battery while it is discharging?** State of charge (SoC) is the fraction of usable charge remaining. It is not measured directly by a sensor, so this project estimates it from measurements that can be collected during operation: voltage, current, and temperature.

Using discharge-cycle data from an LG 18650HG2 lithium-ion cell, the notebook trains a bidirectional LSTM (BiLSTM) to estimate SoC from sequences of those measurements. It then tests the model on separate discharge-cycle files and plots the predicted SoC against reference values derived from the recorded discharge capacity.

- [Notebook in this repository](battery-soc-estimation-bilstm.ipynb)
- [Original Kaggle notebook](https://www.kaggle.com/code/nirmalkrishnas/battery-soc-estimation-bilstm#Predictions-on-testing)

## Run on Kaggle (recommended)

1. Open the original Kaggle notebook and make an editable copy.
2. If the **LG 18650HG2 Li-ion Battery Data** dataset is not already attached, add it as a notebook input. The code expects the `Dataset_Li-ion` directory under `/kaggle/input/lg-18650hg2-liion-battery-data/`.
3. Run the notebook from top to bottom. See **Predictions on testing** for the test-set evaluation and comparison plot.

## Adapt for local use (not tested)

1. Set up Python with Jupyter, TensorFlow/Keras, scikit-learn, NumPy, pandas, Matplotlib, seaborn, Plotly, and pytz.
2. Download the same dataset from the Kaggle notebook's inputs and extract it, preserving the `Dataset_Li-ion` directory structure. The dataset is not included in this repository.
3. Replace the hard-coded `/kaggle/input/lg-18650hg2-liion-battery-data` references with your local dataset path, including the absolute path in the early `25degC` example cell. Skip the `!tree` cell if the command is unavailable.
4. Replace `/kaggle/working/...` with a writable local output directory and create the model-output folders before training. On Windows, change the timestamp format to avoid colons in checkpoint filenames (for example, `%Y%m%d-%H%M%S`).

The notebook is provided as a Jupyter `.ipynb` file; no conversion to `.py` or `.txt` is required.
