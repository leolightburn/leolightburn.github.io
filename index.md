## Latest projects

My current work focuses on improving the intelligibility of noisy speech signals using algorithms based on feed-forward and recurrent neural networks. This research has several possible applications including hearing aids, forensics, and voice communications in adverse environments. In a recent project, working with colleagues in the [Speech and Audio Processing Laboratory](https://www.commsp.ee.ic.ac.uk/~sap/), we integrated one of these algorithms into a [proposed multiple-microphone hearing aid system](https://ieeexplore.ieee.org/document/8521361), leading to substantial improvements in predicted intelligibility in very noisy conditions.

The algorithms have the structure shown below. 

![Overview of a mask-based enhancer](https://leolightburn.github.io/diagrambinarymaskestimator.png)

The input to the algorithm is a noisy speech signal, produced when a desired “clean” speech signal is contaminated by an interfering noise signal. This might be interference from other speakers, or from sources such as car engines, aircraft or machinery. Features are extracted from the noisy speech and used as inputs to an algorithm which uses a neural network to estimate a mask. An example of a mask is shown in (B) in the spectrogram below. The mask has 2 dimensions (time and frequency) and takes values between 0 and 1. The neural network is trained in a supervised manner to estimate a target mask that we [proposed in earlier work](https://ieeexplore.ieee.org/document/7178938). This target mask is based on the clean speech signal, which is unavailable to the mask estimation algorithm. The estimated mask is then applied to the speech in the Short-Time Fourier Transform (STFT) domain, and the signal is converted back into the time-domain. The spectrograms below show the signals labeled A, B and C in the diagram above, alongside the clean speech. In this case, the interfering noise is produced by multiple interfering speakers speaking simultaneously.





## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/leolightburn/leolightburn.github.io/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/leolightburn/leolightburn.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
