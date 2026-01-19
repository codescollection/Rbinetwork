# Rbinetwork

Rbinetwork is an R package designed to recover latent behavioral influence networks and estimate peer influence effects through high-dimensional sparse machine learning. A behavior influence network captures the relational structure among individuals whose actions mutually affect one another within a shared social context—such as a classroom, grade level, or school. In social science research, understanding interpersonal dynamics is crucial, yet a fundamental challenge remains: we often cannot directly observe who influences whom. By reconstructing the underlying “binetwork” from observed behavioral data, this package enables researchers to identify concrete influence pathways—for instance, tracing which peers contributed to an individual’s decision to engage in substance use. Once recovered, the network reveals the full architecture of behavioral influence, allowing for the estimation of peer influence effects, including both the direction and strength of social impact.

Unlike conventional social network analysis—which typically relies on self-reported friendship ties that are costly to collect and prone to measurement error—Rbinetwork provides a novel methodology to infer genuine influence relationships without requiring prior network data. It accommodates both cross‑sectional and longitudinal observation schemes, though the current repository demonstrates implementation for cross‑sectional settings. While the underlying algorithms deliver high estimation accuracy, they are computationally intensive on standard personal computers due to the iterative large‑scale matrix operations involved. Therefore, we have designed parallel computation procedures to improve computational efficiency. We also recommend executing the procedures on high‑performance computing (HPC) platforms, such as supercomputers or computational clusters with high-level CPU cores, to achieve feasible runtimes.

To implement our package, please load the R packages "MASS", “parallel”， “ggplot2"，“gridExtra”， “glmnet", "igraph" and "ivreg" before you running the codes. (For questions or issues, please open an issue on GitHub or contact the maintainer.)


############################################################################
############################################################################

Codes Intrudoction

📋 1. Overview
This R project investigates how different network structures affect the accuracy of network recovery algorithms. The study implements various network generation models, 
a sophisticated network recovery algorithm, and comprehensive evaluation metrics to analyze recovery performance across different topological configurations.


✨ 2. Enhanced Recovery Algorithm

(1) Optimized Implementation: Reduced optimization loops for computational efficiency

(2) Parallel Computing: Leverages multicore processing for faster execution

(3) Lambda Tuning: Automatic optimization of regularization parameter across multiple values

🚀 3. Required R Packages

install.packages(c("MASS", "parallel", "ggplot2", "gridExtra"))

🚀 4. System Requirements

(1) R version 3.6 or higher

(2) Multi-core processor for parallel execution

(3) Sufficient memory (≥ 8GB recommended for larger networks)

📁 5. Project Structure
├── Network Generation Functions

│   ├── generate_ER_network()      # Random networks

│   ├── generate_WS_network()      # Small-world networks

│   ├── generate_BA_network()      # Scale-free networks

│   ├── generate_community_network() # Community networks

│   └── [Additional network types...]

│
├── Network Recovery Algorithm

│   ├── f_function()              # Primary objective function

│   ├── ff_function()             # Threshold optimization function

│   ├── calculate_metrics()       # Comprehensive performance evaluation

│   └── run_network_recovery()    # Main recovery pipeline

│
├── Network Feature Extraction
│   └── extract_network_features() # Computes topological characteristics
│

├── Research Studies

│   ├── conduct_network_structure_study()    # Impact of network topology

│   ├── conduct_sample_size_study()          # Effect of node count

│   ├── conduct_fixed_edges_vary_nodes_study() # Fixed edges, varying nodes

│   └── conduct_fixed_nodes_vary_edges_study() # Fixed nodes, varying density

│
├── Visualization & Analysis

│   ├── analyze_and_visualize_results()      # Multi-figure analysis

│   ├── visualize_fixed_edges_vary_nodes()   # Fixed-edge study plots

│   └── visualize_fixed_nodes_vary_edges()   # Fixed-node study plots
│
└── Main Execution Functions

    ├── main_network_structure_study()       # Primary study runner
    
    ├── main_sample_size_study()             # Sample size analysis
    
    ├── main_fixed_edges_vary_nodes_study()  # Fixed-edge analysis
    
    └── main_fixed_nodes_vary_edges_study()  # Fixed-node analysis
    

🎯 6. Usage Examples

#Test network recovery on a single scale-free network

result <- quick_test_single_network()

#Compare recovery rates across 8 different network types

study_results <- main_network_structure_study()

#Analyze how node count affects recovery accuracy

sample_results <- main_sample_size_study()

#Investigate recovery with constant edges but varying nodes

fixed_edges_results <- main_fixed_edges_vary_nodes_study()

#Examine density effects with constant node count

fixed_nodes_results <- main_fixed_nodes_vary_edges_study()

📊 7. Primary Outputs

(1) Statistical Summaries: Average recovery rates, standard deviations, standard errors

(2) Performance Metrics: TPR, TNR, F1 scores, MAD values for each network type

(3) Correlation Analysis: Relationships between network features and recovery metrics

vRegression Models: Predictive models for recovery rates based on network characteristics

(4) Visualizations: Comprehensive multi-panel plots comparing performance across conditions


📊 8. Saved Results

(1) All studies automatically save results to RData files:

(2) network_structure_study_results.RData

(3) sample_size_study_results.RData

(4) fixed_edges_vary_nodes_results.RData

(5) fixed_nodes_vary_edges_results.RData


🔬 9. Key Studies Included

(1) Network Topology Impact

Investigates how 8 different network structures affect recovery accuracy using:

- 20-node networks

- 3 repetitions per network type

- 11 lambda values for regularization tuning

(2) Sample Size Effects

Examines recovery performance with varying node counts (10-30 nodes) on ER networks.

(3) Fixed Edge Count Analysis

Holds edge count constant (~50 edges) while varying node count (15-40 nodes) to isolate density effects.

(4) Fixed Node Count Analysis

Maintains constant node count (30 nodes) while varying edge density (0.1-0.5) to study density impact.

🛠️ 10. Technical Details

- Algorithm Optimizations

(1) Reduced optimization loops from original implementation

(2) Parallel processing across multiple cores

(3) Efficient matrix operations for large networks

(4) Network Features Computed

- Density, average degree, degree variance
- 
(1) Clustering coefficient, degree assortativity

(2) Network diameter, number of components

(3) Degree distribution skewness

(4) Statistical Analysis

- Mean comparisons with standard errors
- 
(1) Correlation matrices between features and metrics

(2) Multiple regression modeling

(3) Trade-off analysis between TPR and TNR

⚡ 11. Performance Considerations

- Computation Time

(1) Single network recovery: ~30-60 seconds (depending on node count)

(2) Full structure study: ~15-30 minutes (8 networks × 3 repetitions)

(3) Parallelization: Utilizes (CPU cores - 1) for lambda optimization

(4) Memory Usage

- Scales with O(n²) where n is node count
  
(1) 20-node networks require ~100MB RAM

(2) 40-node networks require ~400MB RAM

📈 12. Visualization Examples

- The code generates comprehensive visualizations including:
  
(1) Recovery rate bar charts with error bars

(2) TPR vs TNR scatter plots

(3) F1 score comparisons across network types

(4) Recovery rate vs network density relationships

(5) Time-series plots for sample size studies

(6) Trade-off analyses between different metrics


🔧 13. Customization Options

- Adjustable Parameters
  
(1) Node count (10-50 nodes recommended)

(2) Edge density (0.1-0.8 typical range)

(3) Number of repetitions (≥3 for statistical reliability)

(4) Lambda range and count (5-15 values recommended)

(5) Network type parameters (k, p_rewire, m, etc.)

(6) Extending the Code

- Add new network generation functions following existing patterns
  
(1) Modify evaluation metrics in calculate_metrics()

(2) Adjust visualization themes in analysis functions

(3) Incorporate additional statistical tests as needed

📚 14. Citation & References

If using this code for research, please cite relevant methodologies from:

(1) Wasserman & Roeder (2009) on high-dimensional variable selection

(2) Classic network models: Erdős-Rényi, Watts-Strogatz, Barabási-Albert

(3) Network recovery and spatial econometrics literature

🤝 15. Contributing

Contributions are welcome! Please:

(1) Fork the repository

(2) Create a feature branch

(3) Add tests for new functionality

(4) Submit a pull request with clear documentation


📄 16. License

This project is provided for academic and research purposes. Please contact the authors for specific licensing inquiries.

⚠️ 17. Known Issues & Limitations

Computational Intensity: Recovery algorithm is computationally expensive for large networks (>50 nodes)

Memory Usage: Dense networks require significant memory

Convergence: Optimization may occasionally fail to converge; results include error handling

Determinism: Random network generation requires set.seed() for reproducibility



<img width="1528" height="514" alt="recovered behavioral influence networks" src="https://github.com/user-attachments/assets/5d67d866-92cf-4227-b9b7-1642efccd783" />
(Recovered bullying influence networks for nine schools by the SML algorithm.
Each panel displays the bullying influence network recovered by Algorithm SML for one
school. Nodes represent students; red circles denote bullies and blue squares denote non-bullies. Directed edges indicate estimated behavioral influence relations. Node size is
proportional to degree centrality. Isolated nodes indicate students with no recovered influence
links.)


