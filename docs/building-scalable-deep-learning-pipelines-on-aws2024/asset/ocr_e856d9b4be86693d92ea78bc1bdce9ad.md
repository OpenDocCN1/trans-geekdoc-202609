# CHAPTER 1    OVERVIEW OF SCALABLE DEEP LEARNING PIPELINES ON AWS

```
```
Project Directory Structure
├── data
│   └── TSLA_stock.csv
├── logs
├── output
│   ├── TSLA_stock.parquet
│   │   ├── _SUCCESS
│   │   └── part-00000-2c717885-1e92-4091-b73e-c07fb2f42ba8-c000.snappy.parquet
│   └── TSLA_stock_train.parquet
│       ├── _SUCCESS
│       └── part-00000-3931d223-097a-4b7f-a6df-6ddc8abfbc5c-c000.snappy.parquet
├── src
│   ├── pyspark_code
│   │   └── data_preprocessing.py
│   ├── pytorch_code
│   │   ├── model.py
│   │   └── model_training.py
│   └── main.py
├── tests
│   └── test.py
├── visualizations
│   └── plot.png
├── README.md
├── config.yaml
└── requirements.txt
```
```

**Figure 1-2.** *Project Directory Structure for Predicting Tesla Stock Price*

To understand the organization of the Tesla stock prediction project, let’s examine the directory structure in detail:

+   - data: This directory contains the input data for the project. In this case, it’s a CSV file named TSLA_stock.csv, containing historical stock data for Tesla.
- logs: This directory might contain log files generated during the execution of the project. It’s common practice to separate logs from other project files for easier management.