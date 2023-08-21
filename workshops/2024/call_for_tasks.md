

## Call for Task Proposals

We invite proposals for tasks to be run as part of SIGMORPHON 2024. SIGMORPHON is the Special Interest Group on Computational Phonetics, Phonology, and Morphology.  We are one of the longest running SIGs in ACL, having just completed our 20th workshop.
SIGMORPHON aims to investigate language at a level smaller than the word.  Phonetics is concerned with the human production of linguistic sounds, while phonology investigates the patterns that emerge from their interaction with each other and other linguistic aspects.  Morphology is concerned with the shaping of words through the application of semi-regular processes that alter the syntactic and semantic categories of the words they operate on.
For SIGMORPHON 2024, we welcome any task that invites participants to further computational knowledge in one of our areas of interest.  

We particularly welcome any task that expands phonological or morphological knowledge in under-resourced languages, or languages with under-studied phenomena (ie, reduplication, tonal languages, polysynthetic languages).
While we welcome any proposal, we will show preference to tasks that can demonstrate the feasibility of their completion within the task timeline (ie, pilot studies that show reasonable initial results are desirable), and can convincingly demonstrate both the need for the proposed task, and enough interest to justify its inclusion in the workshop.  

The goal of our tasks is three-fold: we wish to expand the state-of-the-art in computational phonetics, phonology, and morphology - the task must therefore be relevant to current research.  Secondly, we wish to broaden the participation in SIGMORPHON - the task should therefore not be so difficult that it limits participation.  Finally, we seek to provide standardized data sets that can be benchmarked by the community. 

## Task Selection

Task proposals will be reviewed by the SIGMORPHON executive committee, and reviews will serve as the basis for acceptance decisions. We are looking to accept any reasonable task. Task proposals will be evaluated on:
- Novelty: Is the task on a compelling new problem that has not been explored much in the community? Is the task a rerun, but covering substantially new ground (new sub-tasks, new types of data, new languages, etc.)?
- Interest: Is the proposed task likely to attract a sufficient number of participants?
- Data: Are the plans for collecting data convincing? Will the resulting data be of high quality? Will annotations have meaningfully high inter-annotator agreements? Have all appropriate licenses for use and re-use of the data after the evaluation been secured? Have all international privacy concerns been addressed? Will the data annotation be ready on time?
- Evaluation: Is the methodology for evaluation sound? Is the necessary infrastructure available or can it be built in time for the shared task? Will research inspired by this task be able to evaluate in the same manner and on the same data after the initial task?
- Impact: What is the expected impact of the data in this task on future research beyond the SIGMORPHON Workshop?
New Tasks vs. Task Reruns
We welcome both new tasks and task reruns. For a new task, an aspect to be addressed in the proposal is whether it would be able to attract participants. Preference will be given to novel tasks that have not received much attention yet.
For task reruns, the organizers should in their proposal defend the need for another iteration of their task. Valid reasons for a rerun would be: the need for a new form of evaluation (e.g., a new metric to test new phenomena, a new application-oriented scenario, etc.), the need to test on new types of data (e.g., social media, domain-specific corpora), a significant expansion in scale over a previous trial run of the task, etc.

## Changes for 2024

We are aware of the time constraint issues from the last few years, and appreciate the organizers' efforts in running smooth shared tasks.  This year, we will be trying something new.

* Instead of presenting the results of the shared task in the regular proceedings, we will be creating a second volume of proceedings exclusively for the shared tasks.
This allows us to extend many of the dates for the tasks, as the largest time crunch was preparing the proceedings by the ACL deadline, we hope this will allow for a longer participation period, and encourage more participation.

* Instead of presenting the results of the shared task at the workshop, we are planning to host a special online event solely dedicated to the shared tasks.  We do not come to this decision lightly.  Along
  with allowing for a longer participation timeframe, we also have other justifications.
* Many of our shared task participants are students, and the burden of cost is nearing prohibitive levels for many of them.  We do not want
  to limit participation in the tasks only to those with funding.  Winning systems can still be invited to present at the workshop itself.
* We currently schedule 2-3 hours of our workshop to the shared tasks, which makes for a long day, and limits the other talks and events that we can host at our workshop.

* We are encouraging organizers to require participants to submit their systems to the organizers this year.  Along with facilitating evaluation and analysis, this will allow for easier incorporation of baselines in future years, and also allow for some cross-pollination between systems.
  
## Task Organization

We welcome people who have never organized a SIGMORPHON task before, as well as those who have. Apart from providing trial, training, and test data, task organizers are expected to:
- provide to task participants format checkers and standard scorers.
- provide baseline systems that participants can use as a starting point (in order to lower the obstacles to participation). A baseline system typically contains code that reads the data, creates a baseline response (e.g., random guessing, majority class prediction, etc.), and outputs the evaluation results. Whenever possible, baseline systems should be written in widely used programming languages, and should provide adequate documentation for modification by potential participants.
- verify the data annotations have sufficient inter-annotator agreement, and verify licenses for the data allow its use in the competition and afterward, and any potential security or privacy concerns have been resolved
- create a mailing group (and optionally website) for the task and post all relevant information there.
- write a task description paper to be included in the SIGMORPHON proceedings
- manage participants’ system description submissions to the task; and possibly shepherd papers that need additional help in improving the writing
- review one or two other task description papers

## Proposed timeline for tasks

We are currently planning to extend a proposal for the SIGMORPHON workshop, aiming for a workshop in Summer 2024 (likely NAACL).  We will then host shared tasks results in August, 2024.  This timeline is subject to change.

<li> December 1, 2023: Task website is complete, and accepting registrations to the mailing list </li>
<li> January 15, 2024: Data collection is complete, and data is released to participants </li>
<li> February 15, 2024: Baseline systems released to participants </li>
<li> May 15, 2024: Test data is available for participants </li>
<li> May 31, 2024: Final Submissions are due </li>
<li> June 3, 2024: Results announced to participants </li>
<li> June 22, 2024: System papers due for review </li>
<li> July 31, 2024: Reviews back to participants </li>
<li> August 15, 2024:  CR deadline; task paper due from organizers. </li>


## Important dates

<li> Task proposals due: September 30, 2023 </li>
<li> Task selection notification: October 15, 2023 </li>
<li> Shared Task Workshop: August, 2024 </li>

<br> 
<br>
Tasks that fail to keep up with crucial deadlines such as the dates for having the task website up and dates for training and test data may be canceled at the discretion of SIGMORPHON organizers. Canceled tasks will be encouraged to submit proposals for the subsequent year’s SIGMORPHON.

## Submission Details

The task proposals should be a self-contained document of no longer than 3 pages. References do not count against the page limit. 
All submissions must be in PDF format.
Each proposal should contain the following:
- Overview
-- A summary of the task in general
-- Motivation, why this task is needed and which communities would be interested in participating
-- What the expected impact of the task will be
- Data & Resources
-- How the training/testing data will be built and/or procured
-- What source texts/corpora are going to be used? Please discuss whether existing corpora have been re-used or not.
-- How much data is going to be produced
-- How will quality of the data be ensured and evaluated
-- An example of what a data instance would look like
-- The anticipated availability of the necessary resources to the participants (copyright, etc.)
-- The resources required to prepare the task (computation and annotation time, costs of annotations, etc.) and their availability
-- Details regarding secured or to-be-secured permissions for use of this data by the copyright holders by participants in the SIGMORPHON evaluation and by the research community in perpetuity after the SIGMORPHON evaluation
-- Details that address any potential concerns that could arise with respect to privacy, confidentiality, or security (e.g. if personally identifiable information of private individuals is released or detectable, if medical information is present)
-- Pilot Task
-- Details of the pilot task, if any
-- What lessons were learned and how these will impact the future task design
- Evaluation
-- The evaluation methodology to be used, including clear evaluation criteria
- Proposed baseline(s)
– The baseline system that will be provided to participants.  This is not set in stone (you can change the baseline after the proposal).
- For Task Reruns
-- Justification for why a new iteration of the task is needed, using the criteria discussed above
-- What will differ from the previous instance
-- The expected impact of the re-run compared with the previous instance
- Task organizers
-- Names, affiliations, brief description of research interests and relevant experience, contact information (email) including a single email address that SIGMORPHON organizers can use to contact all task organizers at once.
-- The names of SIGMORPHON tasks you have run in the past along with the year the task was run.
Proposals will be reviewed by the SIGMORPHON executive committee, all of whom have familiarity with recent SIGMORPHON tasks. However, all proposals should be written in a self-explanatory manner and contain sufficient examples.
 
All proposals should be e-mailed to official SIGMORPHON e-mail: sigmorphon@gmail.com; they will then be forwarded to the executive committee.
 
## SIGMORPHON Executive Committee:
 
Garrett Nicolai, University of British Columbia <br>
Miikka Silfverberg, University of British Columbia <br>
Eleanor Chodroff, University of York <br>
Çağrı Çöltekin, University of Tübingen <br>
Fred Mailhot, Dialpad, Inc <br>

Contact: sigmorphon@gmail.com

