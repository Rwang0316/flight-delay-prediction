# Flight Delay Prediction

DSC 148 course project. Predicts whether a U.S. domestic flight will arrive more
than 15 minutes late, using only information known before departure.

## Dataset
2015 Flight Delays and Cancellations (U.S. DOT / Bureau of Transportation Statistics),
~5.8M flights. Download from Kaggle: https://www.kaggle.com/datasets/usdot/flight-delays

Place the three CSV files inside a `data/` folder:
```
data/flights.csv      (large — not committed to git)
data/airlines.csv
data/airports.csv
```

## Setup
```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## Run
Open `flight_delay_prediction.ipynb` in VS Code and run all cells.
Outputs are saved to `figures/` and `results/`.

## Method
- Target: `is_delayed = ARRIVAL_DELAY > 15` (DOT standard)
- Leakage columns (departure delay, actual times, delay reasons) are excluded
- Feature engineering: time-of-day, season, weekend flag, airport historical delay rates
- Baselines: Logistic Regression, Random Forest
- Final model: LightGBM
- Analysis: ablation study, feature importance, hyperparameter sensitivity
