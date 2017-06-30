---
layout: post
title:  "Install TensorFlow with GPU for Windows 10"
date:   2017-01-22 01:25:00
author: Nitish S. Mutha
categories: TensorFlow
tags:	tensorFlow windows deepLearning machineLearning google python gpu cpu
cover:  "/assets/post001/neural-header.png"
comments: true
---

On November 9, 2015 Google open sourced a software library called TensorFlow. TensorFlow is a software library used for Machine learning and Deep learning for numerical computation using data flow graphs. It can run on multiple CPUs and GPUs.  
Since deep learning algorithms runs on huge data sets, it is extremely beneficial to run these algorithms on CUDA enabled Nvidia GPUs to achieve faster execution.  

When I wanted to install TensorFlow GPU version on my machine, I browsed through internet and [tensorflow.org](https://www.tensorflow.org) for steps to download and setup. I could not find any good and clear source for setting up TensorFLow on local machine with GPU support for Windows. Most of the information available online was for Linux or Mac OS. Most search results online said there is no support for TensorFlow with GPU on Windows yet and few suggested to use virtual machines on Windows but again the would not utilize GPU.  

Then I decided to explore myself and see if that is still the case or has Google recently released support for TensorFlow with GPU on Windows. After refering few pages on [tensorflow.org](https://www.tensorflow.org) I was able to setup TensorFlow GPU version on my Windows machine with ease. So now it is possible to have TensorFlow running on Windows with GPU support.  


## Requirements  
* Python 3.5  
* Nvidia CUDA GPU. You can check [here](https://developer.nvidia.com/cuda-gpus) if your GPU is CUDA compatible.  



## Setting up your Nvidia GPU
You need to install Cuda Toolkit 8.0 and cuDNN v5.1 as the GPU version works best with these.  

**Download and install CUDA Toolkit**  
Toolkit version 8.0 or above: [https://developer.nvidia.com/cuda-downloads](https://developer.nvidia.com/cuda-downloads)  
Example installation directory: `C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0`  

**Download and install cuDNN**  
cuDNN version 5.1 library for Windows 10: [https://developer.nvidia.com/cudnn](https://developer.nvidia.com/cudnn)  
You would need to signup at Nvidia in order to download these files.
Now extract the cuDNN files into your Toolkit directory.  


<a href="/assets/posts/post001/cudnn1.jpg" data-lightbox="falcon9-large" data-title="cuDNN files">
  <img src="/assets/posts/post001/cudnn1.jpg" title="cuDNN files">
</a>

**Environmental variables**  
Ensure after installing CUDA toolkit, the CUDA_HOME is set in the environmental variables. If not then you need to add it manually.. 

<a href="/assets/posts/post001/cudnn2.jpg" data-lightbox="falcon9-large" data-title="cuDNN files">
  <img src="/assets/posts/post001/cudnn2.jpg" title="cuDNN files">
</a>  

And path variables as..

<a href="/assets/posts/post001/cudnn3.jpg" data-lightbox="falcon9-large" data-title="cuDNN files">
  <img src="/assets/posts/post001/cudnn3.jpg" title="cuDNN files">
</a>


## Install Anaconda  

We will install Anaconda as it helps us to easily manage separate environments for specific distributions of Python, without disturbing the version of python installed on your system.  

**Download and install**  
[Anaconda](https://www.continuum.io/downloads)  

**Create conda environment**  
Create new environment, with the name tensorflow-gpu and python version 3.5.2  
`conda create -n tensorflow-gpu python=3.5.2`  

<a href="/assets/posts/post001/conda1.JPG" data-lightbox="falcon9-large" data-title="conda">
  <img src="/assets/posts/post001/conda1.JPG" title="conda">
</a>

**Activate the environment**
`activate tensorflow-gpu`  

<a href="/assets/posts/post001/conda2.JPG" data-lightbox="falcon9-large" data-title="conda">
  <img src="/assets/posts/post001/conda2.JPG" title="conda">
</a>

**Install tensorFlow**  
`pip install tensorflow-gpu`  

<a href="/assets/posts/post001/conda3.JPG" data-lightbox="falcon9-large" data-title="conda">
  <img src="/assets/posts/post001/conda3.JPG" title="conda">
</a>

Done. You have successfully installed TensorFlow with GPU on your Windows machine.  
Now lets test if it is using GPU...

**Activate environment we created**  
`activate tensorflow-gpu`  


**Test GPU**  
Enter into python shell  
`python`  

`import tensorflow as tf`  

Now run this command and check if it identifies your GPU.  
`sess = tf.Session(config=tf.ConfigProto(log_device_placement=True))`  

<a href="/assets/posts/post001/tf.JPG" data-lightbox="falcon9-large" data-title="tf">
  <img src="/assets/posts/post001/tf.JPG" title="tf">
</a>

That's all. Time to play with it.  


{% if page.comments %}
<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/

var disqus_config = function () {
this.page.url = "{{site.url}}{{page.url}}";  // Replace PAGE_URL with your page's canonical URL variable
this.page.identifier = "{{page.id}}"; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
};

(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://nitishmuthagithub.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
                                           
{% endif %}