1.) Intial Labeling: begin with 20 randomly generated frames.

![Labeling Convention](C:\Users\Charlie Kortleven\Desktop\Git\cassi_sleap_strader_lab\sleap_ai\1_labeling_conventions.png)

Labeled 8 points (B1-B8) on the circumference of the jelly's bell. Emphasis here was put on ensuring each point lie precisely on the circumference. The edges (connections between points) will not be factored in to tracked pulsation rates, and instead, were used as a proxy to equidistantly place B1-B8. C1 refers to the center of the jelly's bell.

2.) Model Training: train the model on unseen frames, and correct where necessary

Train on annotated frames -> predict on: random frames (20 total) -> wait for training to fully finish

Go -> Next Labeled Frame -> 'Score' (to view prediction confidence) -> Re-annotate predictions by right-clicking (when necessary)

Continue this 'human-in-the-loop' correction until model can predict frames with high accuracy. 

This took me about 4 rounds of training to get predictions with instance scores consistently > 90%.

3.) Export model 

The specific components of the model depend one which was selected for training. In this case, I used the 'multi-animal top-down' approach, which first finds each jelly (center instance, C1), and then estimates the pose of each found jelly (B1-B8 on the circumference). The resulting model came in two parts: (1) centered instance, (2) centroid. Both are required as inputs for downstream analysis. 
