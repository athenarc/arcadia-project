# Forecasting Resource Demand for Dynamic Server Sizing in Telco Datacenters

Cloud computing technologies in telecommunication infrastructures are undergoing a transformation, driven by energy efficiency regulations. Dynamic server sizing (DSS) presents optimization opportunities for power consumption and resource demands. Accurate forecasting methods for 5G workload demands across multiple resources are investigated and evaluated, showing that simple statistical algorithms can outperform complex ones. The trade-off between single- and multi-output forecasting models is also analyzed.

The current project analyzes 4 Machine Learning algorithms (Linear Regression, XGBoost, LGBM, Neural Network - LSTM) for time series forecasting of workload demans for resources such as CPU, memory, storage, GPU and DPDK. More specifically the workflow of the project includes:

1. Prepare the dataset, generate the features, normalize it and appropriately prepare it for the algorithms
2. Search for the optimal hyperparameters for the algorithms using Bayesian optimization
3. Train the models to the optimal set of hyperparameters and record their performance
