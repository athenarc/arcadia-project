## Telco Datacenter Resource Demands Open Data

This is a collection of telco workloads data accompanied with scripts and additional experiment data. You can also find the data in Zenodo (https://zenodo.org/records/10245448)

### Introduction

Telecommunication cloud services have emerged as crucial components in the contemporary digital landscape, offering extensive capabilities for data management, connectivity, and service provision. However, research on telco cloud environments lacks comprehensive data on the characteristics of production workloads, which are fundamental for optimizing resource management systems. Understanding these workload attributes is pivotal for enhancing the efficacy of resource management mechanisms, including Virtual Machine (VM) schedulers and power management systems, employed within telco cloud providers. Herein a comprehensive dataset that encapsulates crucial information regarding the demands of applications within telco data centers is provided that captures applications’ demands over time in telecommunication data centers. In total, three distinct types of workloads are presented: dynamic, static, and a hybrid mix of both. By incorporating diverse workload scenarios, this designed dataset aims to offer a nuanced understanding of application demands over time within telco data centers.

### Environment

- Software: `Python`
- Python Packages: `pandas`, `matplotlib`

### Structure

```
.
├── data
│   ├── nodes_allocatable.csv.zip
│   ├── pods_request_scenario_A.csv.zip
│   ├── pods_request_scenario_B_*.csv.zip
│   └── pods_request_scenario_C_*.csv.zip
└── notebook
    └── data-plots.ipynb
```

- `data`: Folder that contains all the data
  - `nodes_allocatable`: Csv file that contains nodes information over time. The node files comprise seven columns, each row includes specific node conditions and their specifications (CPU, memory, GPU) at designated timestamps. In instances where the **Status** column isn't _true_ and the **Condition** column isn't _Ready_, it signifies that the node, at that timestamp, isn't actively serving any applications and is closed. The column Scenario distinguish the rows based on the experiment that is described in the table below
  - `pods_request_scenario_A`: Pods resource demands simulating a dynamic workload
  - `pods_request_scenario_B_*`: Pods resource demands simulating a static workload
  - `pods_request_scenario_C_*`: Pods resource demands simulating a balanced (mix of dynamin and static) workload
- `notebook`: Jyputer notebooks for data visualization

### Experiments

In these experiments, we forecast the future resource demands of the datacenter and based on predictions we decide how many nodes you need to serve the load. Through this process, only the necessary number of servers can be active and the rest of the servers can be switched off to minimize energy consumption as well as as to reduce operational expenses. These experiments used the provided workloads to train machine learning algorithms for forecasting future resource demands. Subsequently, decision-making algorithms were implemented to determine the optimal number of nodes required in upcoming hours, aligning with the anticipated demands of pods.

| Scenario | Type                 | Time Period                               | Description / Comments                                                                                                                                                                                    |
| -------: | -------------------- | ----------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|        1 | Data Collection      | 2023-10-13 12:04:00 - 2023-10-16 09:24:30 | Scenario A Pods Demands with Dynamic Workload                                                                                                                                                             |
|        2 | Algorithms Execution | 2023-10-16 09:24:30 - 2023-10-20 11:29:30 | This is the case where the higher cost saving was achieved. It didn’t use overprediction, which means that only essential nodes were active, but with cases of long pending pods that couldn’t be served. |
|        3 | Algorithms Execution | 2023-10-20 11:30:00 - 2023-10-24 08:00:30 | The second better case based on gain. In this scenario, both increased gain and decreased long pending pods were achieved.                                                                                |
|        4 | Data Collection      | 2023-10-24 08:01:00 - 2023-10-25 09:21:30 | Scenario B Pods Demands with Static Workload                                                                                                                                                              |
|        5 | Algorithms Execution | 2023-10-25 09:21:30 - 2023-10-29 08:52:00 | This is the worst case where the demand is fixed and almost all the nodes are up and running. In general, in a static environment, it is difficult to save too much.                                      |
|        6 | Data Collection      | 2023-10-29 08:52:30 - 2023-10-30 11:16:30 | Scenario C Pods Demands with Balanced Workload                                                                                                                                                            |
|        7 | Algorithms Execution | 2023-10-30 11:17:00 - 2023-11-02 08:46:00 | The average case with the balanced workload. Herein, a moderate gain is achieved.                                                                                                                         |

### Contact
