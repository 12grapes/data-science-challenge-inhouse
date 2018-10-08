# data-science-challenge-inhouse

#### Problem:

In our database, we have 3000 profiles of users who did Bunch assessment. Bunch assessment gives a profile/ mindset of a person based on [6 dimensions](https://drive.google.com/drive/u/1/folders/1LoZsZ-smraZsImCb3WEBPQxF3y3RfBgq?ogsrc=32).
These 6 dimensions: Adaptability, Collaboration, Customer-orientation, Detail-orientation, Result-orientation, Integrity were developed by Charles O’Reilly and tested with hundreds of tech companies around the world.

Avery dimension is presented on a scale from 0 to 10. However, the design of assessment makes scores depended on each other. In particular, a person has 30 questions or 30 points that are distributed across these 6 dimensions depending on what dimension person prioritized over the other. Meaning person can’t be high across all dimensions. Some scores should be high others low or every score should be equal to each other.

The goal was to create a profile of a person’s mindset based on their LinkedIn profiles.

To do so we decided to build a model that would predict these 6 dimensions based on data from the linkedin profile. We scraped LinkedIn profiles of these people. Features that were mined from these profiles are the following:

        'num_education': number of education institutions that person attended
        'time_education': number of years that person spent on education
        'phd_edu': 1/0, whether a person has a phd degree
        'ma_edu':1/0, whether a person has a ma degree
        'ba_edu':  1/0, whether a person has a ba degree
        'volunteer':1/0, whether a person had a volunteer experience,
        'Num_jobs': number of jobs that person had,
        'Top_job_category': specialization of a person based on his job titles,
        'average_time_at_position': average time that person spent on positions,
        'age': approximate age of a person based on when they started uni
        'have_summary':  1/0, whether a person has a summary
        'summary_length':  length of a summary
        'have_skills':  1/0 whether person put skills in their profile,
        'skills_length': number of skills that person stated in the skills section
        "dimensions":  scores per dimension based on nlp scoring engine using data from summary and job description

To make this task easier we just created a dummy for every dimension where score that is > than 5 is 1 and the rest is 0. 

Then we trained a classifier for every dimension to predict if a person’s score is > 5. The example of predicted values look the following:

Adaptability: 1
Collaboration: 0
Customer-orientation: 0
Detail-orientation: 0
Result-orientation: 1
Integrity: 0


Next, because the goal was to create a profile of a person but not to give values of dimensions, our product teams created archetypes of people based on scores of dimension’s predicted scores.

Based on a dataset that we used for training we created 3 possible archetypes

For example:

  - Achiever:

  Adaptability: 1
  Collaboration: 0
  Customer-orientation: 0
  Detail-orientation: 0
  Result-orientation: 0
  Integrity: 0

  - Expert:

  Adaptability: 0
  Collaboration: 0
  Customer-orientation: 0
  Detail-orientation: 0
  Result-orientation: 0
  Integrity: 0

  - Catalyst:

  Adaptability: 1
  Collaboration: 0
  Customer-orientation: 0
  Detail-orientation: 0
  Result-orientation: 1
  Integrity: 1

However what we found out that some archetypes appear much more frequent than others.

#### Questions you need to answer:

* How would you improve a model. What kind of features would you add? 
* How would you improve the model to make sure that not only achiever and expert appears in profiles?
* What kind of challenges do you see to build a classifier that would predict these dimensions in general?
* What are pros and cons of building these classifiers?

In repo you will find a link to an example of json file of data that we scrape from LinkedIn. Here is a link to [Notebook](https://jupyter.bunch.ai/notebooks/Data%20Science%20challenge%20in%20house/Data.ipynb) with data.

#### Expected result

Please prepare for us a presentation with answers to this questions
