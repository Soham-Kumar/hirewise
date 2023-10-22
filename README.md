# hirewise

# 1. Named Entity Recognition or Token Classification
a. We are currently using SpaCy for NER, trained on a 200 resume dataset. The current model gives following metrics:
  Precision: 0.79,
  Recall: 0.98,
  F1 Score: 0.88
b. Although these results seem good, such high performance is achieved on the test dataset only. If we try to apply this model on any other OCRed resume text, the results are pathetic.This implies a data with very bad generalizability, as even though the validation and test scores are high, it performs bad in real world data.
c. We were short of hardware required for fine tuning BERT (en_core_web_trf) for NER on this dataset.
d. Even better, almost human level results are achieved from multi-modal (combining both NLP and CV) models like Donut and LayoutLMv3 used for Token Classification. We were short of both dataset and hardware requirements for implementing this.

(The folder ner_spacy contains this task.)

# 2. Salary prediction based on extracted fields from the resume
a. We used a [Campus Recruitment]([url](https://www.kaggle.com/datasets/benroshan/factors-affecting-campus-placement)) dataset from Kaggle. The original intentions were to enter the fields we get from NER to this model, but as the first model didn’t work, we are entering manually extracted data to this model.
b. Metrics: R2 Score = 0.8081537063992291
c. The dataset used here is small both in the number of entries and the fields available for each entry. We can infer a lot more data from the resume, and a better dataset will guarantee even better salary predictions.

(THe folder placement_dataset contains this task.)

# 3. Precise HR Question answering using BART QnA
a. OCRed text from resume can be input to BART as context, which can answer certain predefined questions (which the HR wants to ask to the applicants) based on the input resume text.
b. We tried to use many other transformer based models like BERT, RoBERTa, DistilBERT and T5 for this QnA task, but the output was much worse than expected.
c. Currently these answers needs to be manually selected by the HR personnel (a betterment over manually skimming through the resume and extracting answers to these questions).In future, if we can procure a dataset of resumes and whether the candidate has been selected or not, and which of the projects/skills in his resume matched the job role, then this process of giving a ranking to all the candidates based on these answers can be automated too.

(The folder bart-qna contains this task.)

# 4. Future Prospects : Time-to-Fill Prediction
a. Predict the time required to fill specific job positions based on historical data, market trends, and candidate availability. it enables companies to anticipate and plan for the duration it will take to find suitable candidates for open positions.
b. Due to lack of availability of any such dataset, it couldn’t be implemented.
c. Preparation of dataset: Such a dataset could be made by taking inputs from within an organization, and merging with it market datasets for different sectors.

# 5. Future Plans: An interview review system
a. An interviewee finds it difficult to get a review of how his/her interview went, and manual feedback is not viable every time. Hence, voice recorded interviews can be transcribed, and with an appropriate dataset (a dataset of interview transcripts with annotations along every section - a couple of lines/paragraphs - rating how good/bad the candidate performed in it.) can make a robust interview feedback system.
b. Due to lack of availability of any such dataset, it couldn’t be implemented.
c. Preparation of dataset: To prepare such a dataset, the interviewers must give some time after each interview to annotate (give score) to various sections in the transcript of the interview. The sections could be generated from methods like LDA (Latent Dirichlet allocation).
