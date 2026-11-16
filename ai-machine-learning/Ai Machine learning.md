# AI / Machine Learning Notes (transcription)

Auto-transcribed from `Ai Machine learning.pdf` (OCR + AI correction). Diagrams/tables are approximate.

## Page 1
### Game Playing
#### Min Max
#### Alphabeta pruning
```text
AI
Sess#2
Intro to Game Playing
Min Max
Alphabeta pruning
```

## Page 2
### Machine Learning
#### Linear classifier
#### Non Linear classifier
#### Overfitting & underfitting
```text
Machine learning
learning involves improving task (T)
Performance metric (P)
improved based on experience (E)
learning process
Task : classify email as spam
1- Define Problem:
Data : features (attributes) and labels
2 - Split Data : Training set, Test set
3- model learning - learner algo processes train set, induction algo creates classifier (model) that
maps (features) to outputs (labels)
4- model testing - Run model on test, evaluate confusion matrix
Linear classifier
separate data points with straight line (2D) or
hyperplane (3D)
margin: distance b/w boundary and nearest point
maximum margin classifier choose boundary
with largest margin for better robustness
This is basis for SVMs (Support vector
Non Linear classifier
Machines)
if data cant be seperated by straight line
or
Transform data to higher dimension where it
becomes linearly seperable
Overfitting & underfitting
model too simple fails to
model learns from train
capture patterns = high error
L solution : balance complexity using
techniques e.g regularization or cross validation
underfit overfit
generalization error
error
training error
Tree size
```

## Page 3
#### Curse of Dimensionality
#### No Free Lunch Theory
#### Types of ML
```text
Curse of Dimensionality
As features (Dimensions increase) amount of data needed to train model
grows exponentially.
L solution
use dimensionality Reduction (e.g PCA) to project data
into lower dimension while preserving important patterns
Naive Reduction can distort data
No Free Lunch Theory
No single ML algo best for all problems
- so must know about problem (e.g data distribution, complexity)
to choose algo
Types of ML
1 Supervised : model trained on labeled data (input-output pairs)
Types:
classification: Predict discrete labels (e.g spam vs ham)
multiclass classification : more than two classes
e.g
multilabel class: each example can have multilabel
Regression Supervised : Predict continuous values e.g steering
0-2
find relationship b/w
numeric variables
Unsupervised/Clustering : find pattern in unlabeled data
2
grouping similar data
Anomaly Detection :
Identify outlier
```

## Page 4
### KNN (K-Nearest Neighbour)
```text
Minkowski Distance
KNN
(K-Nearest neighbour)
both for regression, classification
To classify what x is (apple/orange) check neighbors distance
manhattan
euclidean
K value determines how many neighbors to check
sweetness
oranges
Manhat : Σ |I1^p - I2^p|
Adv
Disadv
Euc : sqrt(Σ (I1^p - I2^p)^2)
- easy
- scale
- few hyperparameters (k, distance)
- curse of dim
- Adaptable
- overfitting
- All computation occurs at classification time rather than learning
Q1,
IMDb
Duration
Genre
8.0 (Mission Imp)
160
Action
6.2 (Gudda2)
170
A.
7.2
168
Comedy
o for K nearest choose
majority category
8.2
165
C
find 'barbie' genre with 7.4,
114 duration
Euclidean dist with each neighbor
D(8,160) = sqrt((7.4-8)^2+(114-160)^2) = 46
D(6.2,170) = sqrt((7.4-6.2)^2+(114-170)^2) = 56
D(7.2,168) = sqrt((7.4-7.2)^2+(114-168)^2) = 54
D(8.2,165) = sqrt((7.4-8.2)^2+(114-165)^2) = 41
K nearest neighbor K=1 so 41 = D(8.2,165) so Comedy
K=3 — 46, 41, 54 => Action, Com, Comedy => Comedy (Majority)
```

## Page 5
#### Optimal K
#### Cross validation
#### Time Comp
#### Weighted KNN
```text
- Manhattan vs Euc
To Do
- Time complex
- How to find K value
Optimal (K=?) → Find experimentally
start K=1, use test set validate error rate
repeat K=K+2 (should be odd to avoid ties)
choose k with least value of error rate
split data
train, test, eval
train
Cross validation
try each validation, avg result
eval
fold1 | F2 | F3 | F4 | test
f1 | f2 | f3 | f4 | test
f1 | f2 | f3 | f4 | test
Time Comp
= m × n
instances
features in
for continuous value or handling ties
in dataset
axis (sweetness, texture, size...)
points plotted
weighted KNN
each neighbor's contribution to prediction is weighted by inverse of distance = 1/dist
```

## Page 6
### Decision Tree
```text
Decision T
L mainly used for classification but can also do regression
root node will have most info gain
Q1/
Feature
class
Red
Blue
B
Green
A
C
''
Entire entropy = H(S) = Σc -pc log2(pc)
= -[PA log2(PA) + PB log2(PB) + PC log2(PC)] = 1.48
probability PA = 5/10 = 0.5 ...
PB = 0.3, PC = 0.2
Info gain for Red
Red → H(S_red) = -[PA/red log(PA/red) + PB/red ... ] =
```

## Page 7
#### Information Gain
```text
why not binary
Humidity
Play Football?
yes
Q
Weather
Temp
Wind
Day
1
Sunny
High
Weak
No
entropy = -yes/total - No/total
Hot
2
S
H
H
Strong
N
Cloudy
3
H
H
W
Yes
4
Rain
Mild
H
W
R
Cool
Normal
W
Y
R
5
6
C
N
S
R
C
N
7
S
Y
8
C
M
H
W
N
H = -
Σ
i=1
9
S
C
N
W
Y
10
S
M
N
W
Y
Pi = Probability of occurrence of i
High H = all classes equal
R
M
11
N
S
Y
M
12
13
14
Entire Entropy
Info
gain of Weather
9 log2
S[9,5]
=
0.94
14
14
14
14
9 yes 5 Nos
Pyes
PNo
sum of all possible Yes, No, Maybe
step2) Entropy of all attributes
Entropy of sunny = [+2,-3]
= -2/5 log2(2/5) - 3/5 log2(3/5)
= 0.97
Cloudy [+4,0]
= 0
Rain (+3,-2)
= 0.97
(Total decisions of attribute)
step3) Information Gain = Entire(Entropy) - Attributes
= 0.94 - 5/14 Ent(S)
- 5/14 Ent(R)
4/14
Ent(C)
IG of weather =
0.246
```

## Page 8
```text
(Cold)
Hot
mild
Info gain of Temp = Ent(Entire) -
Ent(Hot)
4
14
IG
Temp
=
0.029
Humidity
IG of Humidity
0.15
IG wind
0.478
Rain
IG weather
0.246
Sunny
Cloudy
Now find next attribute for sunny by Info gain
so Day
Weath
Temp
Hum
Wind
F
1 S H H W N
2 S H H S N
9 S M H W N
10 S C N W Y
12 S M N S Y
IG of Temp = Ent(Sunny) -
Ent(Attributes)  c
= 0.57
Total
IG(Sunny, Temp) = 0.57
IG(Sunny, Humid) = 0.97
weather
IG(Sunny, Wind) = 0.0197
so
Rain
Sunny
Cloudy
Yes
humidity
High
Normal
Now Rain
info gain etc.
```

## Page 9
### Kmeans Clustering
```text
Kmeans Clustering
Assume
Iteration 1
c1(20,500) | c2(40,1000)
Distance
Q1)
sr-no
age
amount
C1
20
c1
C2
40
c1
1000
c2
C3
30
800
C4
300
18
After iteration 1 update centroid c1 = mean(c3 +
C5
28
1200
C6
25
1400
c2 = mean(c
C7
45
1800
K1
K2
assign any two values to
each cluster K1, K2 in this case c1, c2
40,1000
calculate
for C3
=> d(C3,K1) = sqrt((30-20)^2+(800-500)^2) = 300
Distance from centroids
d(C3,K2) = sqrt((30-40)^2+(800-1000)^2) = 200
Select nearest centroid, add c3 to that Cluster K=
→ K2 so
K2
(c2,c3)
update centroid
L mean of c2, c3 so
40+30
1000+800
=
(35, 900)
2
2
Repeat for Rest
Adv of kmean
Disadv
→ efficient = O(N·K·T)
→ sensitive to initial centroid
pool points not clusters
→ Requires 'k' in advance
→ guaranteed termination
→ Works only if mean defined : doesn't work on categorical data
→ Not always optimal
```

## Page 10
### Heirachical Clustering
```text
Heirachical Clustering
- No backtracking
Q1)
1
5 8 10 19 20
1) Distance matrix
7
9
5
4
3
5
Dendogram
(1,(5,(8,10))),(19,20) ⑤
steps 1,2,3,4,5
(1,(5,(8,10))) ④
combine lowest
5,(8,10) ③
distance point into cluster (1)
(8,10) ②
(19,20) ①
20
5
8
10
19
Adv Heirachical
vs
KMean
→ Doesn't need 'K', not required to be specified
→ Fixed K
→ Based Dendogram (flexible)
→ Slower O(N^2)
→ Faster O(N·K·T)
→ Not
→ sensitive to initial centroids
→ detailed analysis, flexible
→ large dataset, fixed cluster
```

## Page 11
#### Single linkage cluster
```text
Single linkage cluster
take minimum distance centroids
cluster
complete linkage
Sample_no
Single Linkage
Q1
X
Y
S1
4
3
S2
1
4
S3
2
1
S4
3
8
6
9
S5
S6
step1)
Proximity Matrix (Distance)
: euclidean
S1
S2
2.82 5.09
S1
S4
S5
S6
S2
0
3.16
6.32
2.23
0
3.16
4.47
7.07
S3
7.07
8.94
3
S4
0
3.16
7.28
S5
0
8.06
S6
0
step2) single linkage so min value for r => 2.23 = S6,S1 so (S1,S6)
(S1,S6)
S1,S6
S2
S3
S4
S5
0
3.16
2.82
5.09
6.32
step3) Now again min value = 2.82 = S3,(S1,S6)
0
3.16
4.47
S2
7.07
S3
S1,6,3
S2
S4
S5
0
7.07
8.44
S1,6,3
0
3.16
5.09
6.32
3.16
S2
0
7.07
step4) min = S1,6,3 + S2 ,
S4+S5
```

## Page 12
#### Evaluating cluster quality
```text
S4,S5
(S1,S6,S3),S2
0
4.47 5.09
S4,S5
4.47 5.09
0
Dendogram
S1 S6 S3 S2 S4 S5
Evaluating cluster quality
Good cluster have
1) High intra cluster similarity : Points within cluster close (Low variance)
2) clusters well separated
high
(xi - x̄)^2
variance = spread of point =>
Var(x) = 1
N-1
i=1
```

## Page 13
#### DB index
```text
DB index (Davies Bouldin)
L To evaluate cluster quality
Rij = var(ci) + var(cj)}
intra
DB = 1/K Σ Ri ,  Ri = max Rij
K    i=1
||ci - cj||  } inter
cluster
separation
Goal = minimum DB
```

## Page 14
### Performance analysis
```text
Performance analysis
Confusion matrix
Classifier made total 150 prediction
'yes 100 times', no '50' time, in reality 100 = disease, 50 don't
Predicted No | Predicted Yes
50 total  Actual No
45 = TN
TN    FP
5 = FP
Actual yes
5 = FN
95 = TP
100
100 people actually of which 5
predict wrongfully as No
and 95
have disease
correct as yes
Accuracy = correct Prediction
45+95
= 93.3
All predictions
45+95+5+5
misclassification =
wrong predictn
= 6.67
or Recall
Sensitivity (TP rate)
TP
=
ratio of actual Positive correctly classified
TP / Actual Total Positive
TP+FN
Specificity (TN rate) = TN
TN+FP
Precision
was positive actual
(how many times correct)
=
TP
```

## Page 15
#### Estimating model accuracy
#### Improving Accuracy
```text
Low FP, low FN ideal
medical
estimating model accuracy
Holdout Method
Test
Training
Random subsampling L doesnt rely on test set
1
K fold cross validation
N fold
eval criteria
worst | Ultra Liberal
+
O P
N O
-
O
Perfect Classifier Actual + P
O
O
ultra conservative
always (-)
speed: Time to reach model
Robustness : ability to handle noisy data / missing data
Scalability : handle large dataset efficiently
Goodness of Model : the model should fit problem well (e.g decision tree of
Interpretability : result easy to understand
appropriate size)
improving Accuracy
Bagging : Train model on different subset of data, avg their prediction
Boosting : Train model sequentially, with each new model focused on
correcting errors of previous
random Forest : combine multiple decision trees, each
```

## Page 16
### Neural Network
```text
Neural Network
L mimic human brain, fast at cognition, perception
but slow = numerical calculations
neuron
synapse
L weight
Neuron
Y
Activation Function
Σ xi wi
v =
i=1
Step
Sign
sigmoid
Linear
-1
+1
y = 1/(1+e^-x)
input
linear combiner    hard limiter
output
threshold
Perceptron adjusts its weights to minimize error
if e(p) > 0 increase Weight
e(p) = Yd(p) - Y(p)
e(p) < 0 ↓W to ↑output
actual
desired
```

## Page 17
#### Training Algo
#### MLP
```text
Training Algo
initialize: weight, threshold (θ)
Activation : compute each output
weight update : calculate error, update w
Repeat
Q1)
x1 | x2
Limitation Percep
Only linear problems AND, OR
MLP
L has a hidden layer in b/w i/o layer
Backpropagation
or hyperbolic y = tanh(x)
Activation Func : Sigmoid = 1
1+e^-x
```

## Page 18
#### Accelerating MLP
#### Back Prop
```text
Accelerating MLP
1 use hyperbolic instead of sigmoid
2
Momentum Term
Adaptive learning rate (α) based on error
y3
x1 = 0.35
0.3
Sigmoid, Actual output = 0.5
Q1)
w14 = 0.4
learning rate = 1
O5
y5
w23 = 0.8
H4
0.9
w24 = 0.6
x2 = 0.9
weighted input
sigmoid
, yj = F(aj)
Forward Pass :
y3
aj = Σi (wij × xi)
a1 = (0.1×0.35)+(0.8×0.9) = 0.755
y3 = 1
1+e^-(0.755)
= 0.68
a2 = (0.35×0.4)+(0.9×0.6) = 0.68
= 0.6637
y4 = 1
1+e^-(0.68)
a3 = (0.3×0.68)+(0.9×0.6637) = 0.801
y5 =
= 0.69
1+e^-(0.801)
error = actual - calculated = 0.5-0.69 = -0.19
target
Back Prop.
learning rate
correct teacher output
Δwij = η δj oi
δj = oj (1-oj)(tj - oj)  if output unit
δi = oj(1-oj) Σk δk wkj
if hidden
k
```

## Page 19
### Crypto Arithmetic
```text
calculated
Actual
y4 = 0.6637
y(1-y)(ytarget - y)
δ5 =
= 0.69(1-0.69)(0.5-0.69) = -0.0406
for hidden layer output at 3
δ3 = y3(1-y3) w35 * δ5
= node output
(1-node output)(next weight * next output)
= 0.68(1-0.68) 0.3 * -0.0406
= -0.00265
weight
leading to output
δ4 = 0.6637(1-0.6637) 0.9 * -0.0406 = -0.0082
compute new weights
Δw45 =
η δ5 y4 = 1 * -0.0406 * 0.6637 = -0.0269
error
measure
w45
new
=
0.9 +
-0.0269 = 0.8731
old
Δ
→ Δw35 =
1 (-0.0406)(0.69)
Crypto Arithmetic
SEND + MORE = MONEY
carry
must have carry (1)
so ①
m = 1
② S = 9
M(1) O(0) R E
③ O = 0
M O(1) N(1) E(1) Y
7 = E
P = N
R = 6 X 50
so
E = 6, N = 7
R = 8
9 S
```
