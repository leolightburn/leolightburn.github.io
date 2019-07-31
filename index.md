# Latest projects

My current work focuses on improving the intelligibility of noisy speech signals using algorithms based on feed-forward and recurrent neural networks. This research has several possible applications including hearing aids, forensics, and voice communications in adverse environments. 

In a recent project, working with colleagues in the [Speech and Audio Processing Laboratory](https://www.commsp.ee.ic.ac.uk/~sap/), we integrated one of these algorithms into a [proposed multiple-microphone hearing aid system](https://ieeexplore.ieee.org/document/8521361), leading to substantial improvements in predicted intelligibility in very noisy conditions.

The algorithms have the structure shown below. 

![Overview of a mask-based enhancer](https://leolightburn.github.io/diagrambinarymaskestimator.png)

The input to the algorithm is a noisy speech signal, produced when a desired “clean” speech signal is contaminated by an interfering noise signal. This might be interference from other speakers, or from sources such as car engines, aircraft or machinery. Features are extracted from the noisy speech and used as inputs to an algorithm which uses a neural network to estimate a mask. An example of a mask is shown in (B) in the spectrogram below. The mask has 2 dimensions (time and frequency) and takes values between 0 and 1. The neural network is trained in a supervised manner to estimate a target mask that we [proposed in earlier work](https://ieeexplore.ieee.org/document/7178938). This target mask is based on the clean speech signal, which is unavailable to the mask estimation algorithm. The estimated mask is then applied to the speech in the Short-Time Fourier Transform (STFT) domain, and the signal is converted back into the time-domain. 

The spectrograms below show the signals labeled A, B and C in the diagram above, alongside the clean speech. In this case, the interfering noise is produced by multiple simultaneous interfering speakers.

![Spectrograms](https://leolightburn.github.io/SpectrogramsMaskedSpeech.png)

From the spectrograms, we can see that the mask (B) captures the spectro-temporal amplitude modulation in the clean speech (the pattern of energy in the spectrogram), which is important for speech intelligibility. Compared to the noisy speech (A), the masked speech (C) has a modulation pattern which is closer to the pattern in the clean speech.

## Neural network architectures 
Neighbouring "frames" of speech are highly correlated in time and this can be exploited when estimating the mask.
...

## Audio examples

Further details of these algorithms will be published in two upcoming journal papers, and in my thesis.


# Publications

* A. Moore, L. Lightburn, W. Xue, P. Naylor, and M. Brookes, [Binaural mask informed speech enhancement for hearing aids with head tracking](https://ieeexplore.ieee.org/document/8521361), in *Proc. Intl Wkshp Acoustic Signal Enhancement*, Tokyo, 2018
* L. Lightburn, E. D. Sena, A. Moore, P. A. Naylor, and M. Brookes, [Improving the perceptual quality of ideal binary masked speech](https://ieeexplore.ieee.org/document/7952238), in *Proc. IEEE Intl. Conf. on Acoustics, Speech and Signal Processing*, 2017.
* L. Lightburn and M. Brookes, [A weighted STOI intelligibility metric based on mutual information](https://ieeexplore.ieee.org/abstract/document/7472702), in *Proc. IEEE Intl. Conf. on Acoustics, Speech and Signal Processing*, 2016.
* L. Lightburn and M. Brookes, [SOBM – a binary mask for noisy speech that optimises an objective intelligibility metric](https://ieeexplore.ieee.org/abstract/document/7178938), in *Proc. IEEE Intl. Conf. on Acoustics, Speech and Signal Processing*, 2015.
