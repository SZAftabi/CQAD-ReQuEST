# CQAD-ReQuEST
<p align="justify">
CQAD-ReQuEST is a new dataset produced via modifying CQADupStack, a public benchmark dataset for community question answering (https://github.com/D1Doris/CQADupStack). CQAD-ReQuEST is well-suited for joint learning of <i>recognizing question entailment (RQE)</i>, <i>query-focused question summarization (QFQS)</i>, and <i>tag generation (TG)</i> tasks. In other words, it enables us to optimize all the tasks concurrently rather than successively training them with distinct datasets. 
</p>

![CQAD-ReQuEST](./CQAD-ReQuEST.jpg?width=600?raw=true)


<b> CQAD-ReQuEST is constructed through six steps:</b><br>
<ul>
  <li align="justify">
    At first, five features are extracted for each question, including ID, body, title, tags, and IDs of duplicate questions. <br>
  </li>
  <li align="justify">
    In the second step, the questions having less than 70 tokens are picked out of this collection. The new collection contains 202304 questions and 7346 pairs of duplicates. <br>
  </li>
  <li align="justify">
    The third step is to create four samples per each question pair. To clarify, let Q<sup>1</sup> and Q<sup>2</sup> be a pair of duplicate questions. Hence, the body of Q<sup>1</sup> is coupled with the body of Q<sup>2</sup> to form a new sample. The second sample is made by associating Q<sup>1</sup>  title with Q<sup>2</sup> title. This process is repeated by coupling Q<sup>1</sup> body with Q<sup>2</sup> title and vice versa. Then, the created samples are added to a new empty dataset. <br>
  </li>
  <li align="justify">
    The fourth step is to compare the first sequence of each sample with the second sequence and swap them if necessary so that the first sequence is always the longest. From now on, we will refer to them as long and short text, respectively. <br>
  </li>
  <li align="justify">
  In the fifth step, each sample is completed by appending the tags of both texts and the long text title. <br>
  </li>
  <li align="justify">
    In the last step, all samples are labeled 1, which means they belong to the entailment class. Furthermore, the same procedure is applied for non-duplicate questions, except that the labels are 0.
</li>
</ul>
<p align="justify">
We also provide a small size of CQAD-ReQuEST, named CQAD-ReQuEST<sub>small</sub>, containing a subset of 10000 samples.
</p>
