# Rbinetwork

Rbinetwork is an R package designed to recover latent behavioral influence networks and estimate peer influence effects through high-dimensional sparse machine learning. A behavior influence network captures the relational structure among individuals whose actions mutually affect one another within a shared social context—such as a classroom, grade level, or school. In social science research, understanding interpersonal dynamics is crucial, yet a fundamental challenge remains: we often cannot directly observe who influences whom. By reconstructing the underlying “binetwork” from observed behavioral data, this package enables researchers to identify concrete influence pathways—for instance, tracing which peers contributed to an individual’s decision to engage in substance use. Once recovered, the network reveals the full architecture of behavioral influence, allowing for the estimation of peer influence effects, including both the direction and strength of social impact.

Unlike conventional social network analysis—which typically relies on self-reported friendship ties that are costly to collect and prone to measurement error—Rbinetwork provides a novel methodology to infer genuine influence relationships without requiring prior network data. It accommodates both cross‑sectional and longitudinal observation schemes, though the current repository demonstrates implementation for cross‑sectional settings. While the underlying algorithms deliver high estimation accuracy, they are computationally intensive on standard personal computers due to the iterative large‑scale matrix operations involved. Therefore, we have designed parallel computation procedures to improve computational efficiency. We also recommend executing the procedures on high‑performance computing (HPC) platforms, such as supercomputers or computational clusters with high-level CPU cores, to achieve feasible runtimes.

To implement our package, please load the R packages "MASS", “parallel”， “ggplot2"，“gridExtra”， “glmnet", "igraph" and "ivreg" before you running the codes. (For questions or issues, please open an issue on GitHub or contact the maintainer.)

<img width="1528" height="514" alt="recovered behavioral influence networks" src="https://github.com/user-attachments/assets/5d67d866-92cf-4227-b9b7-1642efccd783" />
(Recovered bullying influence networks for nine schools by the SML algorithm.
Each panel displays the bullying influence network recovered by Algorithm SML for one
school. Nodes represent students; red circles denote bullies and blue squares denote non-bullies. Directed edges indicate estimated behavioral influence relations. Node size is
proportional to degree centrality. Isolated nodes indicate students with no recovered influence
links.)


