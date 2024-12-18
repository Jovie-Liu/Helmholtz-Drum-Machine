# Helmholtz-Drum-Machine
Real-time Music-generating User-computer Interactive Helmholtz Machine

This repository records an application that performs real-time machine-learning-based music generating, synthesizing, streaming, and training in Python. The generative model is the Helmholtz machine, and the generated music is percussive drum patterns. The real-time training is instructed by user preference based on-line data construction. The multi-processing real-time system is realized by `threading` in Python.

*Note*: this work is included in the author's Ph.D. qualification writing [Studies based on the Helmholtz Machine](https://drive.google.com/file/d/1CNLO2FjDNW5RT0Zfc70ynZeVdm-KQsTH/view?pli=1), Chapter 4.

## Real-time Multi-processing Interactive System

There are 4 threads in the multi-processing system:

- Thread 1: Streaming. Real-time audio streaming under PyAudio's audio I/O system. Two alternative buffers to write synthesized audio.

- Thread 2: Synthesis. Sample from the Helmholtz machine to synthesize the next drum audio. A bywork is to update the progress bar.

- Thread 3: User control: the user has 3 types of control: like (1 or l), dislike (2 or d), stop (0 or s). The timing of liking/disliking a sample is shifted backwards half of a buffer length. Stop is to terminate the real-time streaming.

- Thread 4: Training: Training of the neural network with real-time user-constructed datasets by active sampling. A bywork is to plot the data and generative distribution after several epochs.

<img src="Figures/real_train.jpg" style="width:800px">
<caption><center> Figure 1: Thread-based Multi-processing System for Real-time audio Streaming, Synthesis, and User-interactive Neural Network Training. </center></caption>
