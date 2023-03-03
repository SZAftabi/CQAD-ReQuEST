# CQAD-ReQuEST

CQAD-ReQuEST is a new dataset produced via modifying CQADupStack, a public benchmark dataset for community question answering (https://github.com/D1Doris/CQADupStack). CQAD-ReQuEST is well-suited for joint learning of recognizing question entailment (RQE), query-focused question summarization (QFQS), and tag generation (TG) tasks. In other words, it enables us to optimize all the tasks concurrently rather than successively training them with distinct datasets. 

CQAD-ReQuEST is constructed through six steps:
At first, five features are extracted for each question, including ID, body, title, tags, and IDs of duplicate questions. 
In the second step, the questions having less than 70 tokens are picked out of this collection. The new collection contains 202304 questions and 7346 pairs of duplicates. 
The third step is to create four samples per each question pair. To clarify, let Q^1 and Q^2 be a pair of duplicate questions. Hence, the body of Q^1 is coupled with the body of Q^2 to form a new sample. The second sample is made by associating Q^1  title with Q^2 title. This process is repeated by coupling Q^1 body with Q^2 title and vice versa. Then, the created samples are added to a new empty dataset. 
The fourth step is to compare the first sequence of each sample with the second sequence and swap them if necessary so that the first sequence is always the longest. From now on, we will refer to them as long and short text, respectively. 
In the fifth step, each sample is completed by appending the tags of both texts and the long text title. 
In the last step, all samples are labeled 1, which means they belong to the entailment class. Furthermore, the same procedure is applied for non-duplicate questions, except that the labels are 0.

During simultaneous multi-task learning, the long and short texts and their label are utilized for the RQE task. Meanwhile, all TG parameters are learned using long texts as input sequences and long text tags as target sequences. For QFQS purposes, if the label is 1, the long text and the short text are regarded as the input sequence and the target summary; otherwise, long texts and their titles are utilized.
This research also provides a small size of CQAD-ReQuEST, named 〖"CQAD-ReQuEST" 〗_"small" , 
