Download Link: https://assignmentchef.com/product/solved-cs1675-homework2-clustering
<br>
In this assignment, you will implement the K-means algorithm. You will then use it to perform image clustering, to test your implementation.

<u>Part I: Clustering</u>)

Write a function <span style="font-family: courier new;">my_kmeans.m</span> to implement a basic version of the K-means algorithm.

<b>Inputs:</b> [5 pts for correct format of input/output]

<ul>

 <li>an NxD data matrix <span style="font-family: courier new;">A</span> where N is the number of samples and D is the dimensionality of your feature representation,</li>

 <li>the number <span style="font-family: courier new;">K</span> denoting how many clusters to output, and</li>

 <li>a value <span style="font-family: courier new;">iters</span> saying how many iterations to run for K-means.</li>

</ul>

<b>Outputs:</b>

<ul>

 <li>an Nx1 output <span style="font-family: courier new;">ids</span> containing the data membership IDs of each sample (denoted by indices randing from 1 to K, where K is the number of clusters),</li>

 <li>a KxD matrix <span style="font-family: courier new;">means</span> containing the mean/center for each cluster, and</li>

 <li>a scalar <span style="font-family: courier new;">ssd</span> measuring the final SSD error of the clustering, i.e. the sum of the squared distances between points and their assigned means, summed over all clusters.</li>

</ul>

<b>Instructions:</b>

<ol>

 <li>[5 pts] First, initialize the cluster means randomly. Get the range of the feature space, separately for each feature dimension (compute max and min and take the difference) and use this to request random numbers in that range. Check the documentation for <span style="font-family: courier new;">rand</span>.</li>

 <li>[5 pts] Then, iterate over the following two steps. The first step is to compute the memberships for each data sample. Use Matlab’s function <span style="font-family: courier new;">pdist2</span> to efficiently compute distances (check its documentation to see what inputs it expects). Then for each sample, find the min distance and the cluster that gives this min distance.</li>

 <li>[5 pts] The second step is to recompute the cluster means, simply taking the average across samples assigned to that cluster, for each feature dimension.</li>

 <li>[5 pts] Finally, compute the overall SSD error. It helps to keep track of the min distance per sample as you iterate.</li>

</ol>

<u>Part II: Random restarts </u>

K-means is sensitive to the random choice of initial clusters. To improve your odds of getting a good clustering, implement a wrapper function <span style="font-family: courier new;">restarts.m</span> to do <span style="font-family: courier new;">R</span> random restarts and return the clustering with the lowest SSD error.

<b>Inputs:</b> same as for <span style="font-family: courier new;">my_kmeans.m</span>, plus

<ul>

 <li>a scalar <span style="font-family: courier new;">R</span> denoting how many random restarts to perform.</li>

</ul>

<b>Outputs:</b> same as for <span style="font-family: courier new;">my_kmeans.m</span>, but

<ul>

 <li><span style="font-family: courier new;">ssd</span> is the lowest SSD across all random restarts.</li>

</ul>

<u>Part III: Image segmentation using clustering </u>(20 points)

You will next test your implementation by applying clustering to segment and recolor an image. Write your code in a script <span style="font-family: courier new;">segment.m</span> .

<ol>

 <li>[5 pts] Download the following images: <a href="https://people.cs.pitt.edu/~kovashka/cs1675_fa18/panda.jpg"><span style="font-family: courier new;">panda</span></a>, <a href="https://people.cs.pitt.edu/~kovashka/cs1675_fa18/cardinal.jpg"><span style="font-family: courier new;">cardinal</span></a>, and <a href="https://people.cs.pitt.edu/~kovashka/cs1675_fa18/pittsburgh.png"><span style="font-family: courier new;">pittsburgh</span></a>. Load them in Matlab using <span style="font-family: courier new;">im = imread(filename);</span>. This will return a HxWx3 matrix per image, where H and W denote height and width, and the image has three channels (R, G, B). Convert the image to <span style="font-family: courier new;">double</span> format. To avoid a long run of your code, downsample the images (reduce their size) e.g. using <span style="font-family: courier new;">im = imresize(im, [100 100]);</span>.</li>

 <li>[5 pts] To perform segmentation, you need a representation for every image pixel. We will use a three-dimensional feature representation for each pixel, consisting of the R, G and B values of each pixel. Use <span style="font-family: courier new;">im = reshape(im, H*W, 3);</span> to convert the 3D matrix into a 2D matrix with pixels as the rows and channels (features) as the columns. Use the random restarts function you wrote above, to perform clustering over the pixels of the image.</li>

 <li>[5 pts] Then recolor the pixels of each image according to their cluster membership. In particular, replace each pixel with the average R, G, B values for the cluster to which the pixel belongs (i.e. recolor using the cluster means). Show the recolored image using <span style="font-family: courier new;">imshow</span>, but convert it to format <span style="font-family: courier new;">uint8</span> before displaying.</li>

 <li>[5 pts] Experiment with at least five different combinations of settings for <span style="font-family: courier new;">K, iters, R</span>. Write a brief report (<span style="font-family: courier new;">report.pdf</span> or <span style="font-family: courier new;">report.docx</span>) documenting your findings about these, and include the image results inside the document.</li>

</ol>

<b>Submission:</b> Please include the following files:

<ul>

 <li><span style="font-family: courier new;">my_kmeans.m</span></li>

 <li><span style="font-family: courier new;">restarts.m</span></li>

 <li><span style="font-family: courier new;">segment.m</span></li>

 <li><span style="font-family: courier new;">report.pdf/docx</span></li>

</ul>