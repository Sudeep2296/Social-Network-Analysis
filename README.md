# Social Network Analysis – Research Collaboration Network

## 1. Project Overview

This project analyzes a **Research Collaboration Network** using Social Network Analysis (SNA) techniques.

Researchers are represented as **nodes**, while collaborations between researchers are represented as **edges**. The project applies three important network centrality measures:

- **Degree Centrality** – identifies researchers with the most direct connections.
- **Closeness Centrality** – identifies researchers who are relatively close to other researchers in the network.
- **Betweenness Centrality** – identifies researchers who act as bridges or intermediaries between different parts of the network.

The analysis was implemented using **Python and NetworkX**, with Pandas, NumPy, and Matplotlib used for data processing and visualization.

---

## 2. Objectives

The main objectives of this project are:

1. To construct a research collaboration network from the given dataset.
2. To preprocess and clean the collaboration data.
3. To calculate Degree Centrality for each researcher.
4. To calculate Closeness Centrality for each researcher.
5. To calculate Betweenness Centrality for each researcher.
6. To identify highly influential and well-connected researchers.
7. To visualize the structure and centrality characteristics of the network.
8. To compare different centrality measures and interpret their significance.

---

## 3. Dataset

### Dataset Name
**ca-netscience Research Collaboration Network**

### Dataset File
`ca-netscience.mtx`

The dataset represents a collaboration network in which researchers are connected based on collaboration relationships.

### Network Statistics

| Property | Value |
| :--- | :--- |
| **Number of Researchers** | 379 |
| **Number of Collaborations** | 914 |
| **Network Type** | Undirected |
| **Nodes** | Researchers |
| **Edges** | Research Collaborations |

---

## 4. Technologies Used

- **Python 3.10**
- **JupyterLab**
- **Pandas**
- **NumPy**
- **NetworkX**
- **Matplotlib**
- **SciPy**
- **Git & GitHub**

---

## 5. Project Structure

```text
Social-Network-Analysis/
│
├── Research_Collaboration_Analysis.ipynb.html
├── ca-netscience.mtx
├── ca-netscience_centrality_results.csv
├── readme.html
└── README.md
```

---

## 6. Data Preprocessing

The original dataset was processed before constructing the network. The preprocessing steps included:

1. **Reading the collaboration data** from the Matrix Market format file (`ca-netscience.mtx`).
2. **Removing missing values**.
3. **Removing self-loops** where a researcher is connected to themselves.
4. **Removing duplicate collaboration records**.
5. **Treating the collaboration relationship as undirected**.
6. **Creating a NetworkX graph** from the cleaned edge list.

The cleaned dataset was then used for network analysis.

---

## 7. Methodology

### 7.1 Network Construction

The collaboration dataset was represented as a graph:
- **Node:** Researcher
- **Edge:** Collaboration between two researchers

The graph was created using NetworkX:
```python
G = nx.from_pandas_edgelist(edges_df, source="Researcher1", target="Researcher2")
```

### 7.2 Degree Centrality

Degree centrality measures the proportion of researchers directly connected to a particular researcher. A higher value indicates that the researcher has more direct collaboration relationships.

The degree centrality was calculated using:
```python
degree_centrality = nx.degree_centrality(G)
```

#### Highest Degree Centrality
Researcher 4 has the highest degree centrality:
- **Researcher 4** = `0.089947`

This indicates that Researcher 4 has the strongest direct connectivity in the network.

### 7.3 Closeness Centrality

Closeness centrality measures how close a researcher is to other researchers based on the shortest paths in the network. A higher value indicates that a researcher can reach other researchers through relatively short paths.

The closeness centrality was calculated on the largest connected component:
```python
closeness_centrality = nx.closeness_centrality(G_largest)
```

#### Highest Closeness Centrality
Researcher 26 has the highest closeness centrality:
- **Researcher 26** = `0.256619`

This indicates that Researcher 26 is positioned relatively close to other researchers throughout the network.

### 7.4 Betweenness Centrality

Betweenness centrality measures how frequently a researcher lies on the shortest paths between other researchers. A researcher with high betweenness can act as a bridge or intermediary between different groups.

The betweenness centrality was calculated on the largest connected component:
```python
betweenness_centrality = nx.betweenness_centrality(G_largest)
```

#### Highest Betweenness Centrality
Researcher 26 has the highest betweenness centrality:
- **Researcher 26** = `0.397184`

This suggests that Researcher 26 plays an important bridging role within the collaboration network.

---

## 8. Centrality Results

The top researchers according to the three centrality measures are summarized below:

| Rank | Degree Centrality | Closeness Centrality | Betweenness Centrality |
| :---: | :--- | :--- | :--- |
| **1** | Researcher 4 | Researcher 26 | Researcher 26 |
| **2** | Researcher 5 | Researcher 95 | Researcher 51 |
| **3** | Researcher 26 | Researcher 51 | Researcher 169 |
| **4** | Researcher 16 | Researcher 231 | Researcher 95 |
| **5** | Researcher 67 | Researcher 100 | Researcher 67 |
| **6** | Researcher 70 | Researcher 52 | Researcher 5 |
| **7** | Researcher 95 | Researcher 5 | Researcher 231 |
| **8** | Researcher 15 | Researcher 44 | Researcher 100 |
| **9** | Researcher 113 | Researcher 234 | Researcher 44 |
| **10** | Researcher 51 | Researcher 297 | Researcher 66 |

---

## 9. Overall Centrality Comparison

For comparative analysis, an additional **Overall Centrality** score was calculated as the mean of Degree, Closeness, and Betweenness Centrality:

$$\text{Overall Centrality} = \frac{\text{Degree Centrality} + \text{Closeness Centrality} + \text{Betweenness Centrality}}{3}$$

> **Note:** Overall Centrality is a project-specific comparative measure and is not a standard NetworkX centrality metric.

### Top Researchers by Overall Centrality

| Researcher | Degree Centrality | Closeness Centrality | Betweenness Centrality | Overall Centrality |
| :---: | :---: | :---: | :---: | :---: |
| **26** | 0.071429 | 0.256619 | 0.397184 | **0.241744** |
| **51** | 0.039683 | 0.247059 | 0.345147 | **0.210629** |
| **95** | 0.044974 | 0.249012 | 0.270163 | **0.188049** |
| **5** | 0.071429 | 0.229648 | 0.250628 | **0.183901** |
| **169** | 0.037037 | 0.215877 | 0.286020 | **0.179645** |
| **231** | 0.037037 | 0.243087 | 0.231654 | **0.170593** |
| **67** | 0.050265 | 0.187686 | 0.255428 | **0.164460** |
| **100** | 0.031746 | 0.232902 | 0.221549 | **0.162066** |
| **4** | 0.089947 | 0.213318 | 0.152056 | **0.151774** |
| **52** | 0.037037 | 0.230628 | 0.156396 | **0.141354** |

---

## 10. Key Findings

- **Researcher 4 – Strong Direct Connectivity:**
  Researcher 4 has the highest Degree Centrality with a value of **0.089947**. This indicates that Researcher 4 has the largest number of direct collaboration connections relative to other researchers.

- **Researcher 26 – Strong Network Position:**
  Researcher 26 has the highest:
  - **Closeness Centrality:** `0.256619`
  - **Betweenness Centrality:** `0.397184`
  - **Overall Centrality:** `0.241744`
  
  Therefore, Researcher 26 is particularly important because of both its proximity to other researchers and its role as a bridge within the network.

- **Different Measures Identify Different Roles:**
  The analysis demonstrates that the researcher with the highest number of direct connections is not necessarily the same researcher who has the strongest bridging position. Therefore, using multiple centrality measures provides a more complete understanding of the collaboration network.

---

## 11. Visualizations

The project includes the following visualizations:

- **Research Collaboration Network**
- **Top 10 Researchers by Degree Centrality**
- **Top 10 Researchers by Closeness Centrality**
- **Top 10 Researchers by Betweenness Centrality**
- **Comparison of Centrality Measures**

These visualizations help understand the structure of the research collaboration network and identify important researchers.

---

## 12. Output File

The calculated centrality values are exported to:
- [`ca-netscience_centrality_results.csv`](ca-netscience_centrality_results.csv)

The CSV contains:
- `Researcher`
- `Degree Centrality`
- `Closeness Centrality`
- `Betweenness Centrality`
- `Overall Centrality`

---

## 13. Conclusion

The project successfully demonstrates the application of Social Network Analysis to a research collaboration network.

The network contains **379 researchers** and **914 collaboration relationships**. Degree, Closeness, and Betweenness Centrality were used to identify different types of important researchers.

The results show that:
- **Researcher 4** has the highest direct connectivity.
- **Researcher 26** has the highest closeness centrality.
- **Researcher 26** also has the highest betweenness centrality.
- **Researcher 26** achieves the highest overall comparative centrality score.

The analysis demonstrates that centrality measures can reveal different structural roles within a collaboration network and can be useful for understanding collaboration patterns and influential positions.

---

## 14. Limitations

- The analysis considers the network structure represented in the provided dataset.
- The analysis does not consider the quality or impact of individual research publications.
- Researchers are represented only through their network relationships.
- The Overall Centrality score is a simple average created for comparative analysis and should not be interpreted as a standard network metric.
- The analysis does not include temporal changes in collaboration patterns.

---

## 15. Future Enhancements

Future work could include:
- Weighted collaboration networks.
- Temporal analysis of collaborations.
- Community detection.
- Eigenvector centrality.
- PageRank analysis.
- Analysis of research domains and publication impact.
- Interactive network visualization.
- Comparison of collaboration networks across different years.

---

## 16. Acknowledgement

This project uses data obtained from the Network Repository.

We acknowledge the Network Repository for providing access to network datasets used for this analysis. Please acknowledge the Network Repository in published materials based on data obtained from the repository.

### Recommended Citation

```bibtex
@inproceedings{nr-aaai15,
  title     = {The Network Data Repository with Interactive Graph Analytics and Visualization},
  author    = {Ryan A. Rossi and Nesreen K. Ahmed},
  booktitle = {Proceedings of the Twenty-Ninth AAAI Conference on Artificial Intelligence},
  url       = {http://networkrepository.com},
  year      = {2015}
}
```

Many datasets available through the Network Repository may have additional citation requirements. Please refer to the individual dataset page and the Network Repository data license and policy for applicable requirements.

- **Network Repository:** [http://networkrepository.com](http://networkrepository.com)
- **Data License and Policy:** [http://networkrepository.com/policy.php](http://networkrepository.com/policy.php)

---

## 17. References

1. Rossi, R. A., & Ahmed, N. K. (2015). The Network Data Repository with Interactive Graph Analytics and Visualization. *Proceedings of the Twenty-Ninth AAAI Conference on Artificial Intelligence*.
2. NetworkX Documentation. [https://networkx.org/](https://networkx.org/)
3. Hunter, J. D. (2007). Matplotlib: A 2D Graphics Environment. *Computing in Science & Engineering*, 9(3), 90–95.
4. McKinney, W. *Python for Data Analysis*. O'Reilly Media.
5. Network Repository. [http://networkrepository.com](http://networkrepository.com)

