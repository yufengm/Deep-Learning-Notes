Chapter 11 - Practical Methodology
-  Determine goals with error metric, build end-to-end pipeline, determine bottlenecks in performance, repeatedly make incremental changes;
- Performance metric: precision, recall, PR curve, ROC-TPrate vs FPrate, F-measure, coverage;
- Baseline Models: copying models from similar task;
- Gather more data;
- Selecting hyperparameters: manual tuning see Table 11.1 for details about hyperparameters; Automatic tuning with grid search or random search(*); model based hpyerparameter optimization;
- Debugging strategies: visualization model; visualize worst mistakes; reason about software; fit a tiny dataset; 
- Compare back-propagated derivatives with numerical derivatives;
- Moniter histograms of activations and gradient;
