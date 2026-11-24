# FUTURE_ML_01 --- Sales & Demand Forecasting

**Intern:** Saurabh Kumar Singh\
**Internship track:** Machine Learning\
**Task:** 1 --- Sales & Demand Forecasting\
**Organization:** Future Interns

## Project objective

Build a forecasting workflow using historical Superstore sales data. The
project aggregates transaction records into a monthly sales time series,
creates time-based and lag features, compares a previous-period baseline
with a Random Forest regressor, and produces a three-month forecast.

## Dataset and preparation

-   Input file: `Sample - Superstore.csv.zip`
-   Date field: `Order Date`
-   Target field: `Sales`
-   Aggregation: monthly sales totals
-   Chronological split: final 20% of eligible periods for testing;
    earlier periods for training.

## Method

The notebook creates trend, month, quarter, day-of-week, day-of-year,
lag, and rolling-mean features. It compares a previous-period baseline
(previous period's sales) with a Random Forest regressor.

## Evaluation results

  Model                              MAE        RMSE   MAPE (non-zero actuals)
  -------------------------- ----------- ----------- -------------------------
  Previous-period baseline     19,389.97   22,560.14                    28.58%
  Random Forest                14,971.53   19,285.92                    19.63%

On this chronological test period, Random Forest has lower error on all
three reported metrics than the baseline. This indicates better
performance on this holdout, not guaranteed future accuracy.

## Future forecast

  Forecast month     Predicted sales
  ---------------- -----------------
  January 2018             32,529.55
  February 2018            34,520.21
  March 2018               42,679.41

These are model estimates, not actual observed sales.

## Test-period observations

The test period covers April--December 2017 (9 monthly observations).
Random Forest predictions are closer than the baseline in some months,
but the model underestimates the large November 2017 sales peak. The
model therefore does not fully capture sudden demand spikes.

## Business interpretation

The forecast may support inventory, staffing, and sales planning.
Businesses should review it alongside current market conditions and
operational knowledge rather than treating it as a guaranteed outcome.

## Limitations

-   Promotions, holidays, price changes, stockouts, and market events
    are not explicitly modeled.
-   The model uses a relatively short monthly history.
-   Recursive forecast errors can affect later forecast periods.
-   Better holdout performance does not guarantee future performance.
-   MAPE is calculated only for test observations with non-zero actual
    sales.

## Suggested repository structure

``` text
FUTURE_ML_01/
├── FUTURE_ML_01_Sales_Demand_Forecasting.ipynb
├── README.md
├── outputs/
│   ├── future_sales_forecast.csv
│   ├── model_evaluation.csv
│   └── test_predictions.csv
└── screenshots/
    ├── historical_sales.png
    ├── model_evaluation.png
    ├── actual_vs_predicted.png
    └── future_forecast.png
```

## How to run

1.  Open the notebook in Google Colab or Jupyter.
2.  Upload the Superstore ZIP dataset to the runtime, or update the
    dataset path in the loading cell.
3.  Run the notebook cells in order.
4.  Review the evaluation table and plots.
5.  Export the forecast, evaluation, and test prediction CSV files.

## Submission note

Before submitting for Future Interns Task 1 review, include the final
executed notebook and output files, verify the dataset-loading
instructions, and ensure all reported results match the executed
notebook.
