# Latest projects

My current work focuses on improving the intelligibility of noisy speech signals using algorithms based on feed-forward and recurrent neural networks. This research has several possible applications including hearing aids, forensics, and voice communications in adverse environments. 

In a recent project, working with colleagues in the [Speech and Audio Processing Laboratory](https://www.commsp.ee.ic.ac.uk/~sap/), we integrated a speech enhancement algorithm based on a neural network into a [proposed multiple-microphone hearing aid system](https://ieeexplore.ieee.org/document/8521361), leading to substantial improvements in predicted intelligibility in very noisy conditions.

My research primarily focuses on a scenario where a speech signal has been contaminated by interfering noise signals, such as other speakers, vehicles, aircraft and machinery, and we do not have access to the original "clean" signal. The goal of our algorithm is to improve the intelligibility of the noisy speech (i.e. the percentage of words understood), as well as its quality (how pleasant the signal is to listen to).

One approach is to use an algorithm with the structure shown below. 

![Overview of a mask-based enhancer](https://leolightburn.github.io/diagrambinarymaskestimator.png)

The input to the algorithm is a noisy speech signal. In the first two (lower) blocks in the diagram, features are extracted from the noisy speech and fed, as inputs, into a neural network. The neural network estimates a "Time-Frequency mask", which has two dimensions (time and frequency) and is bounded between 0 and 1. 

The spectrograms below show an examples of a clean speech signal (top), the speech after being contaminated by noise from multiple interfering speakers (A), the mask produced by the "Estimate TF mask" block (B), and the enhanced speech (C). The labels A, B and C correspond to the labels on the diagram above.

From the spectrograms, we can see that the mask (B) captures the spectro-temporal amplitude modulation in the clean speech (the pattern of energy in the spectrogram), which is important for speech intelligibility. Compared to the noisy speech (A), the masked speech (C) has a modulation pattern which is closer to the pattern in the clean speech.

![Spectrograms](https://leolightburn.github.io/SpectrogramsMaskedSpeech.png)

The neural network is trained in a supervised manner to estimate a target mask that we [proposed in earlier work](https://ieeexplore.ieee.org/document/7178938). This target mask is based on the clean speech signal, which is unavailable to the mask estimation algorithm. The noisy speech is then converted into the time-frequency domain using the Short-Time Fourier Transform (STFT), and estimated mask is applied to the signal. Our [proposed approach to applying the mask](https://ieeexplore.ieee.org/document/7952238) involves using the mask to obtain a probability distribution on the clean speech and incorporating this as prior information into a [modified speech enhancer](https://ieeexplore.ieee.org/document/1001645). Finally, the enhanced speech is converted back into the time-domain. 





<div id="div_audio"></div>
## Audio examples
<p>
<H3>Example 1 - machinery noise</H3>
Noisy speech
<audio preload="auto">
    <source src="/mp3 files/noisy1.mp3">
</audio><br>
Enhanced speech
<audio preload="auto">
    <source src="/mp3 files/MMSEMA1.mp3">
</audio><br>
Clean speech
<audio preload="auto">
    <source src="/mp3 files/clean1.mp3">
</audio><br>
</p>

<p>
<H3>Example 2 - babble (interfering speakers)</H3>
Noisy speech
<audio preload="auto">
    <source src="/mp3 files/noisy2.mp3">
</audio><br>
Enhanced speech
<audio preload="auto">
    <source src="/mp3 files/MMSEMA2.mp3">
</audio><br>
Clean speech
<audio preload="auto">
    <source src="/mp3 files/clean2.mp3">
</audio><br>
</p>

<p>
<H3>Example 3 - helicopter cockpit</H3>
Noisy speech
<audio preload="auto">
    <source src="/mp3 files/noisy3.mp3">
</audio><br>
Enhanced speech
<audio preload="auto">
    <source src="/mp3 files/MMSEMA3.mp3">
</audio><br>
Clean speech
<audio preload="auto">
    <source src="/mp3 files/clean3.mp3">
</audio><br>
</p>

<p>
<H3>Example 4 - jet aircraft</H3>
Noisy speech
<audio preload="auto">
    <source src="/mp3 files/noisy4.mp3">
</audio><br>
Enhanced speech
<audio preload="auto">
    <source src="/mp3 files/MMSEMA4.mp3">
</audio><br>
Clean speech
<audio preload="auto">
    <source src="/mp3 files/clean4.mp3">
</audio><br>
</p>


## Neural network architectures 
From the spectrograms of speech, it can be seen that the signal in neighbouring frames (discrete points in time) is highly correlated, and this correlation can be exploited to estimate the mask more accurately. One approach is to use "windows" of features covering several frames. This is illustrated below. Features within a sliding window (upper plot) are concatenated and used as inputs to a feed-forward neural network, which simultaneously estimates all of the mask values within another sliding window (lower plot). The windows then shift forward by one frame to the position shown by the dotted line, and the procedure is repeated. This produces several mask estimates for each mask bin, which are averaged to produced the final mask estimate. The estimation window (lower plot) is intended to improve performance by averaging several mask estimates, thereby lessening the effect of individual mask estimation errors.

![Sliding feature and estimation windows](https://leolightburn.github.io/slidingfeatureestimationwindow.jpg)

An alternative way of exploiting the correlation in the signal is to use a recurrent neural network with Long Short-Term Memory (LSTM). A single LSTM layer or "cell" is shown below. The LSTM cell contains internal memory in the form of a cell state whose value is controlled by two gates---a forget gate and an input gate. The forget gate controls the amount of information to discard from the cell state, and the input gate controls the degree to which the cell state is updated with new values. When the forget gate is “on” and the input gate is “off”, the cell state remains unchanged over successive frames. This enables LSTMs to retain information in their memory for long periods, whichin turn enables them to model long dependencies between inputs and outputs. 

![LSTM layer](https://leolightburn.github.io/LSTMlayer.JPG)

In two upcoming journal papers, and my thesis, I will investigate different choices of features sets, target masks, estimation algorithms, and methods for applying the estimated masks.

<div id="div_1"></div>
# Publications

* A. Moore, L. Lightburn, W. Xue, P. Naylor, and M. Brookes, [Binaural mask informed speech enhancement for hearing aids with head tracking](https://ieeexplore.ieee.org/document/8521361), in *Proc. Intl Wkshp Acoustic Signal Enhancement*, Tokyo, 2018
* L. Lightburn, E. D. Sena, A. Moore, P. A. Naylor, and M. Brookes, [Improving the perceptual quality of ideal binary masked speech](https://ieeexplore.ieee.org/document/7952238), in *Proc. IEEE Intl. Conf. on Acoustics, Speech and Signal Processing*, 2017.
* L. Lightburn and M. Brookes, [A weighted STOI intelligibility metric based on mutual information](https://ieeexplore.ieee.org/abstract/document/7472702), in *Proc. IEEE Intl. Conf. on Acoustics, Speech and Signal Processing*, 2016.
* L. Lightburn and M. Brookes, [SOBM – a binary mask for noisy speech that optimises an objective intelligibility metric](https://ieeexplore.ieee.org/abstract/document/7178938), in *Proc. IEEE Intl. Conf. on Acoustics, Speech and Signal Processing*, 2015.
