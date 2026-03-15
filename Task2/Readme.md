## Data Preparation and Generalization

In the second task, our goal was to prepare the dataset in a way that allows the model to learn effectively while avoiding overfitting and improving its ability to generalize. We focused on ensuring that the data used for training reflects realistic travel conditions.

Initially, we explored the idea of modifying student locations and applying traffic coefficients to simulate variability in travel conditions. However, we realized that shifting locations would invalidate the original time and distance matrices obtained from the TomTom API. Any change in the coordinates would require recalculating the travel time and distance matrices to maintain consistency between location changes and traffic parameters.

We also observed that using manually estimated coefficients for both location shifts and congestion factors would introduce a large number of parameters, which could reduce accuracy and introduce unnecessary uncertainty into the dataset.

For this reason, we decided to rely on a more reliable and realistic approach by generating new travel time and distance matrices using real-world data.

### Dataset Preparation

On March 11, the team shifted back to using the larger dataset consisting of approximately **4000 locations**, which provides better variability and helps the model generalize better.

Several preprocessing steps were carried out by the team:

- The dataset was cleaned to remove the **144 locations corresponding to our project dataset**.
- The large dataset was divided into **smaller subsets** to make clustering computationally manageable instead of clustering the entire dataset at once.
- Multiple dataset partitions were tested to determine which subsets were suitable for clustering.

### Traffic Coefficient Investigation

We also explored traffic-related coefficients based on previous research papers. After implementing a code inspired by one of the papers, our calculated coefficient was approximately **1.8**. However, further literature review indicated that typical values used in similar studies range between **1.2 and 1.4**, with **1.3** being a commonly adopted value.

### Real Travel Data Using Google API

To improve realism and accuracy, we decided to use **Google Maps API** to obtain real travel time and distance matrices.

Using this approach:

- Real travel time and distance matrices were generated for each subset of locations using Google Maps API.
- This ensures that the dataset reflects realistic travel conditions instead of relying on manually estimated traffic coefficients.

This step significantly improved the quality of the dataset and ensures that the model will learn from **accurate and realistic travel information**, which helps improve the reliability and generalization capability of our solution.

