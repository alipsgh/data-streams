# Data Streams

## Synthetic Data Streams

You find the description of the **Sine1**, **Sine2**, **Mixed**, **Stagger**, **Circles**, and **LED** data streams as follows: 
* **Sine1 (with abrupt concept drift)**: It consists of two attributes `x` and `y` uniformly distributed in `[0, 1]`. The classification function is `y = sin(x)`. Instances are classified as _positive_ if they are under the curve; otherwise they are classified as _negative_. At a drift point, the class labels are reversed.
* **Sine2 (with abrupt concept drift)**: It holds two attributes of `x` and `y` which are uniformly distributed in `[0, 1]`. The classification function is `0.5 + 0.3 * sin(3 * π * x)`. Instances under the curve are classified as _positive_ while the other instances are classified as _negative_. At a drift point, the classification scheme is inverted.
* **Mixed (with abrupt concept drift)**: The dataset has two numeric attributes `x` and `y` distributed in the interval `[0, 1]` with two boolean attributes `v` and `w`. The instances are classified as _positive_ if at least two of the three following conditions are satisfied: `v, w, y < 0.5 + 0.3 * sin(3 * π * x)`. The classification is reversed when drift points occur.
* **Stagger (with abrupt concept drift)**: This dataset contains three nominal attributes, namely `size = {small, medium, large}, color={red, green}, and shape={circular, non-circular}`. Before the first drift point, instances are labeled _positive_ if `(color = red) ∧ (size = small)`. After this point and before the second drift, instances are classified _positive_ if `(color = green) v (shape = circular)`, and finally after this second drift point, instances are classified _positive_ only if `(size = medium) v (size = large)`.
* **Circles (with gradual concept drift)**: It has two attributes `x` and `y` that are distributed in `[0, 1]`. The function of circle `<(x_c,y_c), r_c>` is `(x - x_c)^2 + (y - y_c)^2 = r_c^2` where `(x_c, y_c)` is its center and `r_c` is the radius. Four circles of `<(0.2, 0.5), 0.15>`, `<(0.4, 0.5), 0.2>`, `<(0.6, 0.5), 0.25>`, and `<(0.8, 0.5), 0.3>` classify instances in order. Instances inside the circle are classified as _positive_. A drift happens whenever the classification function, i.e. circle function, changes.
* **LED (with gradual concept drift)**: The objective of this dataset is to predict _the digit on a seven-segment_ display, where each digit has a `10%` chance of being displayed. The dataset has `7` attributes related to the class, and `17` irrelevant ones. Concept drift is simulated by interchanging relevant attributes.

As just mentioned, **Sine1**, **Sine2**, **Mixed**, **Stagger**, **Circles** have only `2` class labels, whereas **LED** has `10` class labels.

Typically, for the purpose of experiment, each data stream contains `100,000` or `1,000,000` instances. In the case of `100,000` instances, drift points may be put at every `20,000` instances in **Sine1**, **Sine2**, and **Mixed**, and at every `33,333` instances in **Stagger** with a transition length of `w=50` to simulate _abrupt_ concept drifts. For the **Circles** and **LED** data streams, concept drifts happen at every `25,000` instances with a transition length of `w=500` to simulate _gradual_ concept drifts. `10%` class noise may also added to each data stream.

You may download the zipped files for each group of data streams from [DropBox Link](https://www.dropbox.com/sh/cx58kb5yctdimln/AADPP__VynluSkHssXwC4DNxa?dl=0).

You find `.zip` files containing 100 `.arff` files for each synthetic data stream in `data_streams/synthetic/`.

## Real-world Data Streams

* **Electricity** contains `45,312` instances, with `8` input attributes, recorded every half an hour for two years from Australian New South Wales Electricity. The classification task is to predict a rise (_Up_) or a fall (_Down_) in the electricity price. The concept drift may happen because of changes in consumption habits, unexpected events, and seasonality [1].
* **Forest CoverType** has `54` attributes with `581,012` instances describing `7` forest cover types for `30 X 30` meter cells obtained from US Forest Service (USFS) Region 2 Resource Information System (RIS) data, for four wilderness areas located in the Roosevelt National Forest of northern Colorado [2].
* **Poker hand** comprises of `1,000,000` instances, where each instance is an example of a hand having five playing cards drawn from a standard deck of 52. Each card is described by two attributes (suit and rank), for ten predictive attributes. The class predicts the poker hand [3].

You may find pre-processed version of these data streams (or datasets) from https://moa.cms.waikato.ac.nz/datasets/. (**Please note that regarding these data streams we do not know where/when concept drifts happen, or even if they contain any concept drifts [4, 5].**)

## Other Benchmark Data Streams

* **Adult**: The original dataset has `6` numeric and `8` nominal attributes, two class labels, and `48,842` instances. `32,561` instances are used for building the classification models. The dataset was used to predict whether a person earns an annual income greater than `$50,000` [6].
* **Nursery**: The dataset consists of `5` classes labelled as  `no_recom`, `recommend`, `very_recom`, `priority`, and `spec_priority`. The number of occurrences of the third and fourth classes are infrequent and we removed them from the dataset, resulting in a dataset consisting of `20,000` instances [7].
* **Shuttle**: The original dataset contains nine attributes, `7` class labels, and `58,000` instances and was designed to predict suspicious states during a NASA shuttle mission [8].

I have created three evolving data streams from these three datasets, you find them in `data_streams/other_benchmarks/`.

<hr/>

<b>References</b>
  <ol>
    <li>Žliobaite I (2013) How good is the electricity benchmark for evaluating concept drift adaptation. arXiv preprint arXiv:13013524</li>
    <li>Blackard JA, Dean DJ (1999) Comparative accuracies of artificial neural networks and discriminant analysis in predicting forest cover types from cartographic variables. Computers and electronics in agriculture 24(3):131–151</li>
    <li>Olorunnimbe MK, Viktor HL, Paquet E (2015) Intelligent adaptive ensembles for data stream mining: a high return on investment approach. In: International Workshop on New Frontiers in Mining Complex Patterns, Springer, pp 61–75</li>
    <li>Bifet A, Holmes G, Pfahringer B, Kirkby R, Gavaldà R (2009) New ensemble methods for evolving data streams. In: Proceedings of the 15th ACM SIGKDD international conference on Knowledge discovery and data mining, ACM, pp 139–148</li>
    <li>Huang DTJ, Koh YS, Dobbie G, Bifet A (2015) Drift detection using stream volatility. In: Joint European Conference on Machine Learning and Knowledge Discovery in Databases, Springer, pp 417–432</li>
    <li>Kohavi R (1996) Scaling up the accuracy of naive-bayes classifiers: A decision-tree hybrid. In: KDD, Citeseer, vol 96, pp 202–207</li>
    <li>Zupan B, Bohanec M, Bratko I, Demsar J (1997) Machine learning by function decomposition. In: ICML, pp 421–429</li>
    <li>Catlett J (2002) Statlog (shuttle) data set</li>
  </ol>

<br/>
<br/>

### Citation

Please cite the following papers if you plan to use the data streams:

1. Pesaranghader, Ali, Herna Viktor, and Eric Paquet. "__Reservoir of Diverse Adaptive Learners and Stacking Fast Hoeffding Drift Detection Methods for Evolving Data Streams__", *Machine Learning Journal*, 2018. <br />
Pre-print available at: https://arxiv.org/abs/1709.02457, DOI: https://doi.org/10.1007/s10994-018-5719-z
2. Pesaranghader, Ali, and Herna L. Viktor. "__Fast Hoeffding Drift Detection Method for Evolving Data Streams__", *European Conference on Machine Learning*, 2016. <br />
Pre-print available at: http://iwera.ir/~ali/papers/ecml2016.pdf, DOI: https://doi.org/10.1007/978-3-319-46227-1_7
3. Pesaranghader, Ali, Herna Viktor, and Eric Paquet. "__McDiarmid Drift Detection Methods for Evolving Data Streams__", *International Joint Conference on Neural Networks*, 2018. <br />
Pre-print available at: https://arxiv.org/abs/1710.02030

<br/>
<br/>

<sub>Ali Pesaranghader © 2019</sub>
