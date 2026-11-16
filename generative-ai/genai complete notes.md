# Generative AI Notes (transcription)

Auto-transcribed from `genai complete notes.pdf` (OCR + AI correction). Diagrams/tables are approximate.

## Page 1
### Neural Network Basics
```text
layer
→ flow.
GENAI
weight → how much it matters
y = w1 x + w0     y = w1x1 + w2x2 ... wnxn
. n var → n+1 parameters
→ Activation fun → for non-linearity
. continuous . derivative at all pts
. One Hot encoding → for multiclassif.
[0|1|0] [1|0|0]
one hot
deriv:
∂y'
∂y' = ∂y × ∂O × ∂H3 × ∂H2 → ∂y
∂H1  ∂O  ∂H3  ∂H2  ∂H1
∂w1
* ∂E/∂w0 = 1
∂E/∂w1 = x.
. η = learning rate
∂w0
∂w1
(0-1).
* Δw1 = -η ∂E
∂w1
w1new = wold + Δw1
. ReLU → ignore -ve val ⇒ (0, max)
↳ leaky ReLU (allows 10% of -ve val)
⇒ (0.1 max)
```

## Page 2
### Learning Paradigms
#### Generative Models
#### Discriminative Models
```text
Supervised
. Unsupervised
. Reinforcement
labelled data
unlabelled data
trial & error
→ similarities
→ feedback to make
task driven
predict next val
→ gener. models
strategy
→ data driven + identify
→ delayed gratific.
clusters
predictions
→ Q-learn, DQN
Generative Models. (generating temp) input output
P(X∩Y)
learn 'joint prob. distribution' P(X,Y) =
P(X∪Y)
→ probabilistic model
→ new data pts similar
eg: Gaussian, Hidden Markov, GANs
Discriminative:
P(X,Y)
learn 'conditional prob' P(Y|X) =
P(X)
→ distinguish b/w pts
→ boundary b/w classes
eg: Logistic Reg, Decision trees, NN
→ Gener + Discrim = GAN
* in NN → Softmax activ. fun for probability [0,1]
* linear ⇒ hyperplane → wx+b = 0
* Searchspace → every pts is a sol.
. ReLU → makes model non-linear.
```

## Page 3
#### Maximum Likelihood Estimation (MLE)
#### Chain Rule and Bayes' Rule
#### Backpropagation
#### Parameters vs Hyperparameters
```text
softmax → mutually exclusive
sigmoid → indep. prob.
. Max Likelihood Estim. (MLE):
statistical method to estimate parameters
. if dataset & model w/ param. (θ)
L(θ) = P(data|θ)
. if indep observ.
L = product of indiv. prob
Chain Rule: p(S1∩S2∩Sn) = p(S1)p(S2|S1) ... p(Sn|S1∩S2∩Sn-1)
Bayes Rule:
p(S1|S2) = p(S1∩S2) / p(S2) = p(S2|S1) p(S1) / p(S2)
p(S2)
p(S2)
Backprop: → based on grad. descent.
error = 1/2 Σ (ŷk - yk)^2
2   n
deriv.
⊖ vanishing gradient prob → due to negligible grad
. Parameters: learned by model (weights, biases)
→ internal to architect.
. Hyperparameters: don't change during training
→ for model generalization
→ ext.
(no. of layers, η, batchsize, convergence speed).
```

## Page 4
### CNN
```text
Correlation (dotprod) → similarity
Horizontal filter
Vertical filter
[-1 0 1; -2 0 2; -1 0 1]
[-1 -2 -1; 0 0 0; 1 2 1]
filter
conv
layers
. CNN → matrix multip. → analyze visual
POOL
Feature extraction
map size by 2.
2) fully conn. & softmax layers added for
classification
→ flattening → 1D
→ Convolution + ReLU → makes non-linear
. strides → how many to move.
. pooling → max / avg
* Convul. ⇒ G[i,j] = Σ Σ
I[u,v]F[i-u,j-v]
u=-k v=-k
kernel ⇒ +
```

## Page 5
#### Dilated Convolution
### Recurrent NN (RNN)
#### Gradient Clipping
#### Regularization
#### Autoregressive Models
```text
. Dilated conv: w/ dilated rate → spacing b/w kernel elements
→ cover larger context.
Recurrent NN to process sequential data & recog
hidden state
* 1-1 = vanilla NN
→ feedback loop
x1
* activ. func mostly ⇒ tanh()
→ Backprop thru time (BPTT) → to calculate error
derivatives
Prob: 1) Vanishing / Exploding grad. 2) difficult
G sol → ReLU, Resnets, batch normalization
→ Gradient clipping → max of grad
1) calcul. grad of loss func 2) determine threshold (t)
3) if (||g|| > t) → g = g × t/||g||
norm of grad
||g||
→ Regularization: 1) Lasso 2) Ridge 3) ElasticNet
(λ) → ↑ strength (↑ underfitting)
best → CNN w/ dilated conv.
. finite memory (MLP)
(NLP + img gen.)
. Autoregressive Models → statistical → time series
. joint distr. (P(x,y)) using conditional dist.
* Receptive field → region of input that affects output
(dil. conv improves this w/o ↑ cost)
```

## Page 6
### PixelRNN
#### LSTM Layers
#### Row LSTM
#### Diagonal BiLSTM
```text
RGB = 256 [0-255]
→ trained upto 12 layers of depth
PixelRNN: predicts pixel w/ 2 spatial dim. →
. discrete prob
softmax
LSTM
Residual connect. + → log-likelihood
+ 2 fast RNN
scores
→ to assig prob to each pixel
↳ p(x) = Π p(xi|x1,x2..xi-1) row by row
. computed in //, gen in seq.
. kernel of 1D conv → k×1
k ≥ 3. input-state
LSTM Layers: recurs state-state
1) Forget Gate → filters out irrel data from memory
past
2) Input // → selects curr. input & selects useful
3) Cell State (Memory update → long term) → past + new inp
4) Output Gate → curr output + hidden state
PixelRNN LSTM: input-state → as 1 . state-state → 1 by 1
2) Row LSTM → 1D conv → unidir. → row by row
→ triangular context . k×1 conv.
↳ produces tensor 4h×n×n output feat. maps.
2) Diagnol BiLSTM → to capture overall context
1) Skew input map in space (easy diag. conv.)
↳ offsets each row by 1
↳ map size = n×(2n-1)
```

## Page 7
#### LSTM Diagram
#### Residual Connections
### PixelCNN
```text
Forget
Long-Term
c(t-1)
c
Input Gate
Tanh
memory
cell state
h
Output
sigmoid
Sigmoid  Tanh
Sigmoid
Gate
h(t-1)
[o_i, f_i, l_i, g_i] = σ(K^hs h_(t-1) + K^is · x)
h
short-term
c_i = f_i · c_(i-1) + l_i · g_i
x(t)
h_i = o_i · tanh(c_i)
hidden
x
cell state
2) input-to-state comp → 1x1 conv, K^is → contribute
4 gates → gen. 4h×n×n Tensor
kernel size
3) state-to-state comp → 2x1 column-wise conv,
4) Output feat. map skewed back to n×n → rmv offs
↳ repeated for each 2 direc.
Residual Connec. shortcuts to skip ≥1 layers → d
↳ adds input of curr. layer to its output
Pixel CNN
. Masked conv. → h feat. split into 3 (RGB).
↳ pred. curr → p_i left + above used as context → R
G → prev. gen pixels + R
B → R & G.
```

## Page 8
#### RNN Forward Pass and Loss
#### GAN Discriminator Loss
#### Padding
#### PixelCNN Masks
```text
RNN
1) Forward Pass: maintains hidden
state
input at t
h_t = tanh(w_h h_(t-1) + w_x x_t + b_h)
Generator → ↑ it's
final
output y_t = W_y h_t + b_y
2) Loss Func:
. MSE . Cross Entropy.
↳ L_T = Σ y log ŷ_T
Discriminator → ↓ ditto
. Maxpooling → not
3) BPTT:
. Mode collapse → can't
↳ same
L_D = y_i log D(x) + (1-y_i)(log(1-D(G(z))))
real
false
. padding → to preserve spatial dim
. same padding → output sz = input sz.
. valid //
→ reduces size
. hidden layer in ANN → feat. transformation
. data augmentation → rotation, mirror.
PixelCNN
Mask to input-to-state.
1) Mask A → only to 1st conv. layer → restricts connec to neigh
& color of curr (already predicted).
2) Mask B → subsequent transition → relaxes A's restricts
→ allowing connect from color to itself
```

## Page 9
### AutoEncoders
#### Denoising AutoEncoder
```text
AutoEncoders
→ encodes input x_i to hidden h → decodes input
from h
bottleneck
z
→ to minimize loss func.
. z → smaller than x → dim. reduction
encoder
↳ to capture meaningful factors
of variation
. output sz = input sz.
. latent dim → neurons in the end of bottleneck
① Denoising
. dim. reduction / feat. learning → reconstruct og from
corrupted input.
(x̂_ij - x_ij)^2
J(w) = argmin 1/m ΣΣ
. req og & noisy input.
```

## Page 10
### Variational AutoEncoder (VAE)
#### ELBO
#### KL Divergence
```text
bell-shaped.
Variational (VAE) → probabilistic → Gaussian
→ bottleneck split → mean vector
latent
↳ std. deviation vector
reparametrization → z = μ + σε → stochastic
vector
↳ ε ~ Norm(0,1)
→ to rmv content, detect anomalies, rmv noise
→ maximizes ELBO
Prior → μ=0 σ=1
KL diverg → checks act. + estim ans after entropy
ELBO → evidence lower bound.
↳ minimize -ve ELBO.
+ KL divergence.
. Reconstruction Loss: ||x - x̂||^2
D_KL = 1/2 Σ (1 + log(σ_j^2) - μ_j^2 - σ_j^2).
if KL diverg b/w q(z|x) & P(z) = ↑
↳ garbage img gen.
if KL diverg wt (β) ↑ → underfit → too constrained
```

## Page 11
### Generative Adversarial Networks (GANs)
#### Generator
#### Discriminator
```text
Gen. Adversial Networks -> unsupervised
-> minmax classif. error loss.
. Discriminator + Generator.
(0,1)
-> compete to capture + replicate variations
. Generator: (G(z))
-> gen. eg = -ve training eg for discriminator
-> input = fixed len. random vector w/ noise
-> aim = for discriminator to identify it as 'Real'
* ↓ its loss
. Discriminator: (D(x))
-> identifies real/fake
-> training data = real + fake data
* ↑ its loss
. Convergence -> hard to identify
-> train D(x) for 1-2 epochs -> repeat
2) '' G(z) '' '' ''
```

## Page 12
#### Noise
#### MinMax loss
```text
. D(x) -> asc the grad
G(x) -> desc '' ''
* Noise -> variation
-> Gaussian (μ,σ)
-> Uniform dist. (-1,1) or (0,1)
. loss func -> dist b/w distr. of gen data + real data
. GAN has 2 loss func 2) Wasserstein loss.
-> Generator training -> Discriminator
1) MinMax:
V(G,D) = E_{x~p*}[log D(x)] + E_{z~p_z}[log(1-D(G(z)))]
* L_G = -L_D = V(G,D)
= ∫ p*(x) log D(x) + p_g(x) log(1-D(x)) dx
. D(x)* = Pd(x) /
Pd(x)+Pg(x) = 1/2 => V(G,D) = -log(4)
-ve -> G(x) improves w/ training, D(x) deteriorates
-> 1 network may dominate -> non-convergence
-> stuck at local minima -> D(x) feedback -> useless
-> Mode collapse.
+ve -> sampling / gen. straightforward
-> no max likelihood est in training
-> robust to overfitting
-> good at capturing modes on distr.
```

## Page 13
#### Mode Collapse and solutions
#### Mini-Batch GANs
```text
for sample (x_i,x_j) where T_b:
T_b(x_i) = Σ_{j=1}^{n} e^{-||θ(x_i) - θ(x_j)||}
. Mode Collapse: can't
-> same outputs
. Solutions:
1) Mini-Batch GANS:
-> D(x) evaluates samples in mini-batches instead
of individually whole ''.
-> access authenticity + diversity b/w them
. Generator: prod. patches of img instead single img
-> allows diversity of samples eval by D(x).
. Discriminator: assess how much gen. samples
deviate from real.
-> computes dist / similarities
-> In Back prop -> D(x) feedback -> update both
(+) -> diverse range of outputs -> stable training
-> faster converg. -> more info for G(x).
2) Supervision w/ Labels.
labelling into of real data
Human
Cat
-> instead of Real/Fake ->
Dog
Truck
Fake
```

## Page 14
#### DCGANs
```text
trained first
. DCGANS
-> G(x) uses transposed conv. layers -> D(x) conv. lay.
-> no preproc -> scaled to tanh -> [-1,1]
-> leakyRelu slope = 0.2, Adam opt.
η = 0.0002, momentum = 0.2
. Image De-duplication: -> to ↓ direct replicas
-> img cropped -> focus on center
rmv noise
. Binarization & Semantic hashing:
threshold >1
similar imgs -> similar binary code
<0
3) Adding Noise
4) Regularization: L1(lasso), L2(Ridge), Elastic
-> replace pooling -> strided conv = D(x),
frac- '' '' = G(x)
-> use batchnorm -> rmv fully-connected hid. lay.
-> use ReLU for G(x), output -> Tanh
-> use leakyRelu for D(x), all layers
```

## Page 15
#### Momentum
#### Transfer learning
#### Conditional GANs
```text
. Momentum: accelerates grad learning by
adding fraction of prev update to curr.
. stable sol. . reduces oscil.
(+) . faster converg.
. Transfer learning, when model trained on 1 task
-> reused / finetuned for a related task.
e.g: when limited data.
-> Input: noise + condition (y)
. GAN cannot overfit
* bits -> divide by 255 -> use sigmoid
Conditional GANs -> conditional data, (class labels/feat
-> to Gen & Discrim. (real w/ correct cond, fake w/ intended
G(z|y) D(x,y)
Maxout layer: divide inputs in grp -> max val
-> more complex func. + ↑ model's cap to handle
non-linear.
```

## Page 16
### Diffusion Models
#### Forward diffusion
#### Reverse denoising
```text
-> Forward diffusion -> fixed -> adds noise
-> depends only on prev img
Gaussian
-> smaller noise -> larger steps
N(0,1)
regulated by variance scheduler
(β_0 ... β_T)
-> Reverse denoising -> gener.
. Markov -> memoryless -> only depends on prev
. CycleGAN. 2gen, 2disc.
Gen -> autoencoder
-> 1) Encoder (conv)
2) Transformer (residual) 3) Decoder (transp conv)
```

## Page 17
### Transformers
#### Attention
#### Components
```text
(+) less training & parallel.
autoregressive
Transformers - RNN/CNN:
-> attention mechanism
-> parallel proc.
-> seq. transduction: -> input seq to output seq.
-> tokens -> fundamental units a lang. model proc.
Attention -> globally / soft
-> assign attention score on basis of context
& query -> based on similarity
-> self-attention (scaled-dot-prod) -> word itself.
-> attention score w.r.t all others + ''
Components
Encoder -> representative learning
(2)
autoregressive.
Stacked self attention
Fully connected layers
Decoder -> gener.
contextual embeds -> ELMo, BERT (into 786 numb/token)
```

## Page 18
### LLM
#### Input Preprocessing
#### Positional encoding
#### Attention Mechanism (scaled dot-product)
```text
semantic meaning
capture
dense, low dim
-> word2vec, Glove, BERT
(1) Input Preproc
sparse high dim
-> Tokenization
-> Bag of Words (BOW)
-> input embeddings = raw input into numerical data
-> dense vector repr. -> continuous-valued vectors
-> fixed length -> floating pt numb.
-> rows = seq length. -> words. rows = seq length
-> positional encoding -> learned/fixed -> pos. info of
tokens.
-> sine / cosine
i=(even) /
i=(odd)
starts w/0
pos
PE (pos,2i) = sin(
10000^(2i/dim))
Final embed = input embed + pos. embed.
(2) Attention Mechanism (scaled-dotprod).
-> distinguishes 3 inputs = Query, Key, Value
-> compares Q w/ K -> for compatibility.
-> dotprod of Q w/ all keys divided by √dim_k
-> output -> weighted sum of val.
scaling
```

## Page 19
#### Attention functions
```text
dim = 5x5
words in
sent.
Attent(Q,K,V) = softmax(
QK^T
) V
√dim_k
-> softmax -> row wise -> norm. attent.
scores
to stop vanishing
-> Loss entropy
= J^(t)(θ)
grads.
-log ŷ
x_{t+1}
for total
Mat Mul
L = 1/T Σ -log ŷ
Softmax
x_{t+1}
Mask
Attention func
Scale
1) Additive -> compatibility using
Mat Mul
feed-forward w/ 1 hidden layer.
2) Multiplicative -> softmax (QK^T)V.
faster
Attention Score = QK^T
-> End -> linear layer + softmax -> prob.
. Self attent -> same token for all 3 inputs
Cross '' -> '' '' '' K & V, diff for Q
* Transformers -> neural networks to understand text
& relationship w/i text.
```

## Page 20
### CycleGAN
#### Encoder
#### Transformer (residual)
#### Decoder
```text
G: X→Y
don't require pair data
F: Y→X
CycleGAN -> 2 gen + 2 disc.
Generators -> autoencoder -> unpaired dom.
-> takes img -> extract feat -> gen. img.
3 stages:
1) Encoder (convul): 2D
3 2D conv. layers: -> downsampling.
-> Inst. normaliz. layer -> across each channel
-> ReLU activ.
-> Feat. extraction
. Inst. norm -> (+) ↑ convergence, ↓ hyperparam. sensitivity
2) Transformer (residual):
-> 6 to 9 resid. blocks
-> block = set of 2D conv. layer, BatchNorm,
ReLU
3) Decoder (transp. conv).
-> has 2 upsampling blocks
. transp. conv layer w/ ReLU . ↑ sz of img output
-> at end gener. has 2D conv. layer -> tanh activ. func
```

## Page 21
### StyleGAN
```text
. Losses
1) Adversial → to create realistic.
2) Cycle consistency → if 1 domain to another &
back ⇒ similar
→ prevents learned mapping to contradict
→ acts as regularization → L1 norm
Discriminators → 2
. Dx → real X from fake img of F
. Dy → " Y " " " " G
Total generator loss = Adv_G loss + Adv_F loss + λ. cycle loss
StyleGAN
from
unsupervised sep. of highlevel attr & stochastic variat
⊕ ↑ disentanglement → control diff aspects
↑ interpolation
→ style of 1 and apply to other
traditional → latent code directly in network
Style → latent code transformd via mapping network.
```

## Page 22
#### Mapping network
#### AdaIN
```text
→ have constant input
→ Adaptive Inst. Normal. (AdaIN) controls feat.
→ noise → stochastic variation
. latent space = imp. feat of data
Mapping
→ 8 fully connected layer(MLP) maps z to intermed
→ Affine transf. applied to W
→ converts late
↳ linear transf + translation
nection to style
y = w·W_aff + b_aff
→ y=(y_s,y_b) → used in AdaIN
→ feat map scali
& shifting
→ AdaIN → after each conv. layer in syn. network
→ allows style specific control
↳ normal. by channel-wise mean + variace
then → scales & biases feat by affine tranform
AdaIN (x_i,y) =
x_i - μ(x_i)
y_s,i
σ(x_i) + y_b,i
```

## Page 23
#### Synthesis network and noise
#### Frechet Inception Distance
#### Mixing Regularization
```text
→ Synthesis N/W → 18 layer → each uses AdaIN for
style control
→ Gaussian noise added after each conv. per pixel
↳ each layer has dedicated noise
→ Noise ⇒ gen. fine-grained details → local only
→ Per channel ⇒ scaling factors control noise impact
Frechet Inception Dist
→ to measure gen.ing quality (distr. of feat.)
→ ↓ FID, better quality
→ style GANs ⇒ 20% improv. in FID
. Mixing Regularization:
to avoid dep on single latent code (w1 & w2).
1) Random Crossover: rand. layer selection →
switches from w1 to w2.
⊕. diversity . improves disentanglement.
. styles at diff layers → decorrelated
```

## Page 24
### Diffusion Model
#### Forward diffusion
```text
var = s^2
s.d = √s^2
Diffusion Model
for
→ gen.
simple to gradually complex & real
. Denoising dif. models aka "score-based gen. mod
↳ data change likelihood.
↳ gen. high quality by reversing adding noise.
Gaussian
→ Markov chain → slowly add noise & learn to
reverse dif. process.
→ learned w/ fixed procedure.
. Denoising dif.M: (fixed)
1) Forward dif. : slowly add noise to input
output mean.
var
identity
q(x_t | x_t-1) = N(x_t; √(1-β_t) x_t-1, β_t I)
matrix
var schedule
. β_T → large . β_0 → small
0 ≤ β_t ≤ 1
↳ controls noise input at each step ᾱ_T = ∏α_i
x_t = √ᾱ_t · x_0 + √(1-ᾱ_t) ε — Gaussian noise
noisy
↳ = ∏(1-β_i)
vers.
```

## Page 25
#### Reverse denoising
#### Latent Diffusion Model (LDM)
```text
z_0 → z_t
memoryless
→ each step depends on prev. only. = Markov chain
→ Dif. kernel = formula for noise inc.
↳ Gaussian conv.
2) Reverse denoising (gen). → learned
→ loss → MSE
||ε - ε_θ(x_t,t)||^2
p_θ(x_t-1 | x_t) = N(x_t-1; μ_θ(x_t,t), Σ_θ(x_t,t))
. Dif. Model = VAE
except → encoder = fixed → latent var = same dim
→ denoising model shared among timestep
⊖ comp. cost . slow . memory-intensive
. Latent Dif.M (LDM) → instead of direct dif on
ND input → to smaller latent space.
↳ cross attention layers introduced
⊕ . reduces memory + time . ↓ dim. latent space
→ use UNet
. pre-trained encoder (VAE) → compresses img →
forward reverse → decoder = clean latent repr back to
high-quality img.
```

## Page 26
#### CLIP
#### U-Net
```text
CLIP → contrastive lang. Img Pre-Training
↳ Text encoder.
LDM = CLIP + UNet + VAE + cross attention b/w
ResNet blocks
Cross attention → focus on diff parts of 1 piece
of info. while processing another.
U-Net
1) . Encoder → downsampling → feat. extraction
. Decoder → upsampling
. Skip connec. → directly connect encoder layer
w/ decoder (to access high-freq. info) → to
avoid loss.
2) ResNet Blocks → skip connec. w/ themselves
to help w/ grad. flow.
3) Time Step conditioning → time t converted
to embeds. & put in ResNet
4) Cross-attention layers → Q, K, V.
```

## Page 27
### Vision Transformer
```text
→ need large dataset b/c no built-in priors
↳ must learn spatial
Vision Transformer relations
↳ patches rather than pixels.
. split imgs to patches (tokens). → patch embed
→ ViT → usually use encoder.
→ patch → fixed
1. → flatten the patches in vector
↳ project in lower dim. using linear layer.
3. produce lower-dim linear embed. → flatten
patch thru + positional encoding.
4. Layer Norm (LN)
multihead self-attention
5. encoder has →
→ feed-forward NN. → multi layer perceptron (MLP)
6 → classif. by MLP (1 hidden layer). → <CLS>
↳ aggregates global info via self-attention.
→ Token at start → classif. token → for MLP.
⊖ has less img-specific inductive bias than CNNs.
. no. of patches + 1 (<CLS>) = patch length.
```

## Page 28
### LLM
### BERT
```text
lang. modelling
fine tuning
wanting indiv. under
LLM
1) Tokenization → Bag of words (BOW) → then
combine all unique words → vocabulary
↳ word2vec → captures context.
. LLM → probabilistic
1) Lang. Modelling
→ unsupervised
→ pretraining
↳ focuses on our next word. → NSP
⇒ result model = foundation/base model
2) Fine Tuning
→ post training
→ supervised.
BERT
bidirec encoder reps. from tranformers
→ multi token pred.
→ for sentiment analysis + named entity recog.
```

## Page 29
#### Pre-training tasks
#### Fine-tuning
```text
64 TPUs trained for 4 days
. Pre-training tasks
1) Masked lang. Modelling (MLM) :
hiding a word in a sentence & forcing BERT
to use bidir. to predict it. → context
add cls (classif) & sep tokens
2) Next Sentence Prediction (NSP).
Input
→ relationship b/w sentences
Token embed
. Token embed → start <CLS> & b/w
Segment embed
sentences <SEP> tokens
Position emb
. Segment embeds → each token has
marking for A & B
. Position embed → to show pos.
* <CLS> always interacts w/ all others → capture
info from all other tokens
→ Q & A + inference.
. Fine-tuning
1) on Text-classif: → assigning label to a piece of txt
```

## Page 30
### GPT
```text
2) on Question Answering:
→ BERT replaces 80% w MASK b/c doesn't appear
during fine training → reduce mismatch b/w pre-fine
. Bert Base → 12 layers 768 "
, 12 att
" Large → 24 " , 1024 nodes , 16 att
* BERT tags by predicting tags at each word
piece.
GPT
decoder only
→ focuses on predicting future tokens in a seq
. GPT-4 ⇒ multimodal → text & img input
. 1.76 T param
GPT-5 improv:
. ↓ hallucinations
. ↑ instruc. following
. ↓ sycophancy → post-trained w/ sycophancy scores
(insincere flattering)
```

## Page 31
### Deep Seek
```text
. GPT-5 trained w/ reinforcement learning → for
reasoning → RLHF
. Jailbreaks : prompts to bypass model refusal.
Deep Seek
Mixture of Experts + MLA
→ Total = 67B param → at a time = 37B param
→ uses multihead latent attention
→ supervised fine-tuning & reinforc → RLAIF
. MOE → scale cap. w/ low computation cost.
FT
. Post-training
. distillation filters → transfer reasoning abilities
from R1 to V3.
. verification + reflection patterns → reasoning + correct
```

## Page 32
#### Architecture
#### RMSNorm
#### MoE
```text
Architecture
. Transformers w/ MLA + DeepseekMoE.
. auxillary-loss-free load balancing
RMSNorm → 1) sqrt(1/d Σ x_i^2) = RMS(x)
2) Norm = x
⊙ γ —
learnable
scale
RMS(x)
param
MoE
element wise
multip.
↳ Router → learned module → which expert to
process each token
→ computes score for each expert → selects topK
(2-4).
→ router → usually linear + softmax.
S = W_r h_t
1) Shared Expert → used by all tokens
2) Routed "  →
" " per-token
→ each expert → separate MLP block. → same structure
→ diff. weights
④ saves computation + cost.
Results merged back for next transf.
```

## Page 33
#### Auxillary-loss-free Load Balancing
```text
. Auxillary-loss-free Load Balancing
↳ routing collapse = overuse of few experts
→ unbalanced expert load.
→ MoE uses auxillary loss to force spread of
tokens
. V3 uses routing bias mechanism → add b_i to
each expert.
bias update
if too many tokens → ↓ b_i - γ
speed.
" " few " →
↑
b_i + γ
```

## Page 34
### Autoencoders
### Prompt Engineering
#### Temperature
#### Top P
```text
Autoencoders
Prompt eng.
→ compress & reconstruct data.
Prompt Engineering
0.2
Temperature → 0.0 - 2.0 → for controlling randomness
of output
→ hyperpar. used in softmax during txt gen.
facts based QA
logits to prob.
Temp influences diversity & certainty
→ ↓ Temp, ↑ deterministic. → highest prob chosen
→ ↑ temp → ↑ randomness + diversity → ↑ creative.
poem gen.
e^(z_i/T)
T=1 → Norm SM
P_i =
T>1 → flatter dist
Σ_j e^(z_j/T)
(↑ rand)
T<1 → sharper dist
(↑ confident)
Top P → controls diversity / output gen.
0.0-1.0 → alt. to temp
→ only considers top p whose cumul. prob > threshold p
```

## Page 35
#### Max length
#### Stop Sequence
#### Freq. Penalty
```text
. model first calcul. prob for all next words
↳ sorts by prob + adds to nucleus until
sum > threshold p.
↳ only words w/i nucleus considered for
rand. sampling
either temp or topp, not 2gether
exact + factual → top p ↓
→ " " ↑ → more words even
diverse+
the less likely ones
Max length → no. of tokens model gen.
→ prevents long, irrel. responses
→ controls cost
Stop Sequence → string that stop model gener.
→ another way to control length
Freq. Penalty → penalty to next tokens ∝ appearance
count in resp+prompt
→ ↑ freq. penalty, ↓ likely to appear.
→ reduces repetition
```

## Page 36
#### Presence Penalty
#### Why prompt engineering?
#### Elements
```text
. Presence Penalty → penalty same for all repeated
tokens
→ prevents too often repetition
→ diversity → ↑ pres. penalty
→ focused → ↓ " "
Why prompt engineering? GenAI sensitive to phrasing.
Good prompt → ↑ accur. → change tone or style → control output format → ↓ hallucination
→ save computation by ↓ trial & error.
. Tone, role assig, COT
Elements
1) Instructions →
Inst, I/O, Context
2) Context
3) Input data
4) Output Indicator → type / format
```

## Page 37
#### Self-Refine
### RAG
```text
3) selecting most consist. ans
reasoning path r_i → final ans a_i
→ Self-Refine
Input
feedback
Refine
Model M
1
2
. 3 prompts = init. gener. + feedback + refine
RAG
→ retrieval based → from ext. srcs.
↳ to any data → txt, img, audio
. LLM are knowledge cut off. → hallucinations
→ Hallucination reasons:
. inference
. flawed data srcs
. archit. flaw → training
RAG has:
. Generator → LLM / AI model. (GPT/Gemini).
```

## Page 38
#### Ingestion
```text
. Retriever → Activeloop, Pinecone, langchain
. Ingestion → retrieval → synthesis
Ingestion
. Chunking → dividing data/prompts → encoded
to an embedding vector.
→ smaller chunks → finer precise match.
. Embedding → converting prompts + doc into format
for compared relevance
→ Sparse → high dim space → more vector elem=0
eg: TF-IDF for lexical matching
→ semantic → BERT → capture contextual
info → more resrcs
. Vector DB → stores embedding for similarity
-based searches → query the db to search
↳ cosine similarity / Euclidean dist
↳ KNN.
→ Prompt temp
Sys, history, context, user
```

## Page 39
#### Response
#### RAG vs Fine-tuning
```text
Response
gener. relevant response → not info but aligns
w/ query
→ can't finetune w/ dynamic data
Parametric → weights + biases three training
→ knowledge stored in weights+biases
↳ math. form
Non-Parametric → explicit data accessed directly
Use Rag: . knowledge large/fast-changing
→ lower setup cost + easy updates
→ unstruct. text data and not labelled
→ model to ref. actual doc
Use fine-tuning: → high quality labeled data for
specific task
→ ↓ inference latency → stable domain
```

## Page 40
### Multimodal RAG
```text
Limitation of trad. RAG
↳ works w/ txt doc only → can't ans diag, fig
Multimodal RAG → txt & non-txt content
Components:
1) Multimodal Input Encoder:
Vision/Speech/text encoder.
2) Vector Store/ Index.
-stores embed. txt+img+audio
-supports similarity search
3) Retriever:
→ picks most relevant among modalities
4) Fusion Model / LLM
combines retr. infor → reasoning + ans gene
→ shared embed. space
→ Txt split into → passages
Imgs " " → scenes, obj, bounding boxes
Audio " " → segments
```

## Page 41
### Model Context Protocol
```text
USB-C
Model Context Protocol
connect AI appl to ext. sys.
data src  tools  workflows
→ access key info & perform tasks
⊕ ↓ develop. time + complex. access to sys.
local/remote
→ Client-Server arch.
coordin. MCP host connect to ≥1 MCP server
↳ 1 MCP client for each " "
1-1 direct conn.
→ MCP uses JSON schema for valid.
↳ tools may need user consent
• MCP client → elicitation: req. specific info from
users
• roots → def. filesys boundaries → URIs
↳ don't enforce security restric.
```

## Page 42
### Voice AI
#### Realtime streaming
### GenAI
#### BLEU
```text
Voice AI
STT
LLM ⟹ TTS
Speech → Txt ⟹
(process)
(back to audio)
Realtime streaming:
WebSocket
HTTP
unidire, 1 time conn
handshake
GenAI
(use case)
Model
(model)
(prompting)
Fine tune/(Eval)
yo format
QA
supervised
reinforcement
quantative → MT → Txt Gen → Summ.
• BLEU biling. eval understudy
→ how close gen.txt is to ref Texts (ground truth)
→ calculates prec. of n grams
```
