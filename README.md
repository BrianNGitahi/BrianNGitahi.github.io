# Demos on how to use CEBRA 

This repository contains a concise demo and example on how to use CEBRA with your datasets.
It will regularly be updated with more examples.

For first-time users, the Basics notebook is a good place to start. It contains snippets and examples from the original CEBRA demos on their website: https://cebra.ai/docs/demos.html (refer to these for more details).

Once you have a basic idea of how CEBRA works and you want to use it on your data, take a look at the examples starting with the AIND-Data notebook. 

If you have trouble installing CEBRA you can refer also to this page: https://cebra.ai/docs/installation.html



\begin{abstract}
    This document summarizes the jupyter notebook, AIND-DATA, that shows a preliminary demo on how to use CEBRA with AIND data. It will cover the formatting of data from the Fibre Photometry pipeline of 4 Neuromodulators (DA, 5HT, ACh, NE) recorded in the Nucleus Acumbens region. It will also briefly describe the labels used with CEBRA and explain one set of embeddings. 
\end{abstract}


\section{Formatting Data}

In this foraging task, the mouse is given a binary choice, to lick right or left on each trial. Each choice the mouse makes is either rewarded or unrewarded. For this analysis, we want to view the neural data in a 1 second window around the choice time at each trial in the session. The hope is that this will make it easy to identify the presence/absence of reward in the neuromodulator signal.

In the preliminary analysis, we only considered trials where the mouse made a choice. For each of these trials, we found the timestamp of the dF/F signal that was closest in time to the time of the choice. We then used this temporal information to get the 10 preceding and subsequent dF/F signal values from the `choice time'. 

\section{Behaviour Labels}

CEBRA has both supervised and unsupervised modes of learning the embedding space. In the supervised mode, also known as CEBRA-Behaviour, the user defines labels to be used to classify the input data. These labels can be continuous or discrete. In this analysis, each trial was labelled as rewarded/unrewarded. 

\section{Example Embedding}

\begin{figure}
    \centering
    \includegraphics[scale=0.5]{12.png}
    \caption{\textbf{CEBRA Embeddings showing separation of trials into rewarded (light blue) and unrewarded (purple) from one session}}
    \label{fig:enter-label}
\end{figure}

From this pair of embeddings we can see that there is a clustering of the rewarded (light blue) and unrewarded (purple) trials when we use CEBRA behaviour. The CEBRA-Time embedding is used as a control here. CEBRA-Time embedding is constructed using the unsupervised mode and so the labels we defined earlier to group trials into rewarded and unrewarded were absent in this case.


\section{Next Steps}

The obvious next steps are to try this on all trials and include a third label, `no choice' and see how well CEBRA can separate all three. We would also like to define and use other behavioural labels that we think are directly related to the recordings of the NMs in this task. This example only shows CEBRA using discrete labels so one of the next examples will aim to show CEBRA using continuous labels. This particular embedding also doesn't show the relative contribution of each Neuromodulator to the separation of trials based on reward.
