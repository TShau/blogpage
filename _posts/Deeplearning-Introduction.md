The origin of Deep Learning comes from the inspiration of hierarchical architectures of neural network systems by stacking several layers of learning blocks for feature learning.
Multiple levels of learning blocks enable different representations and abstractions of the previous level as input.
Training those layers makes it possible to make sense of raw data and create a good representation of it.

The below figure exemplifies different levels of feature representation with images.
The input for the first layer is the raw pixel data from the image.
After further abstraction to higher levels, whole objects can be recognized from the raw pixel input.
Being able to understand abstract features enables better learning of specific tasks.
What makes Deep Learning so promising is the efficient computing of those features compared to laborious hand-crafted methods for feature extraction.
Most Deep Learning architectures involve artificial neural network models, like deep belief net-works, deep Boltzmann machines, or convolutional neural networks (CNN).

![image-center]({{ site.url }}{{ site.baseurl }}/assets/pics/Deeplearning-representation.png){: .align-center}

For a better understanding, the following sections introduce Deep Learning, starting with basic machine learning models like neural networks to deep structured CNN.
In the process, the mathematical background, architecture, and diverse techniques of machine learning shall be explained.

## Neural Networks
Machine learning is a discipline in computer science that covers algorithms and models that learn from given data to classify or predict previously unseen data. 
What makes it unique is that tasks are handled without explicit programming. 
Instead, machine learning concentrates on designing models, which learn from input data to make predictions or decisions based on similar data. 
This allows those models to manage complex problems where manual rule-based imperative methods fail. 
When training a model, it is given a massive amount of training data. 
In supervised learning, the set of training data consists of an input object and an expected value. 
A supervised learning algorithm is designed to learn from these examples to do a prediction of the expected value with a given input. 
In the case of unsupervised learning, training data consists only of input objects without labels or expectations. 
Machine learning algorithms can also be viewed as a functionf(θ,data), where the set of model parameters. 
After training, the model parametersθf unaware updated to a point where a function is approximated, which can make a correct prediction out of the input.

''
Todo functions
''
