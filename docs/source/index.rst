Crowdsourcing Tutorial! 
===================================
1. Demo 
2.	Introduction to AMTurk 
3.	How to access to AMTurk via python? --Boto3
4.	How to host the annotation tool and images
5.	During and after data collection: Review results and conduct quality control
6.	My suggestions 

Demo
----------------

 


Qualification:
https://visualgrounding.ischool.utexas.edu/qualification?groupindex=qualification_0
Main task:
https://visualgrounding.ischool.utexas.edu/index?groupindex=train_0
Visualization:
https://visualgrounding.ischool.utexas.edu/visualization?groupindex=test_1
（I haven’t upload the annotation results to server…The following picture is viewed in localhost）
 
 

Introduction to AMTurk
-----------------------------
Amazon Mechanical Turk is a crowdsourcing website for businesses (researchers) to hire remotely located "crowdworkers" to perform discrete on-demand tasks that computers are currently unable to do.

You should read this documentation to get familiar with AMTurk: https://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/

(1)	Use ExternalQuestion if your task is complicated.
Use AMTurk Interface or QuestionForm if your task is simple.
https://docs.aws.amazon.com/AWSMechTurk/latest/AWSMturkAPI/ApiReference_ExternalQuestionArticle.html
 
(2)What will workers see?
https://workersandbox.mturk.com/  
 

2. How to access to AMTurk via python? --Boto3
See BOTO3’s document: 
https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/mturk.html

With Boto 3, you can 
(0)	Access to MTurk
See python script “environments.py” 
If you are developing, use the enviroment ”sandbox”.
If you are in producting mode, use the enviroment ”live”.

 
 
(1)	Check account balance 
 
(2)	Create HITs
See python script “create_tasks.py”
 
(3)	Delete HITs
 
(4)	Create Qualification
 

(5)	Associate Qualification with worker
See python script “associateQ.py”
 
(6)	See Results
 
(7)	Notify workers
See python script “NotifyWorker.py”
 
….
ANYTHING you do via AMTurk interface, you can do via Boto3 instead!

Other tips:
(1)	Qualification example
 


 

3. How to host the annotation tool and images
-------------------------------------------------
You can host it on any server, including GitHub and CU Boulder’s server. 
I would suggest to host it on the CU Boulder’s server

4. Review results and conduct quality control
-------------------------------------------------
To review the result, see “how to access AMTurk-see Results” section.

You can set up rules to conduct quality control, including:
(1)	Results alignments among workers.
(2)	Monitor the time the worker spent on each HIT. 
(3)	If it is a segmentation task, you can calculate the number of points used to draw the segmentation and calculate the IoU overlap between workers to see the annotation agreement.

My suggestions…
-------------------------------------------------
1.	Launch the HITs in a scheduled interval. Write explicitly the scheduled interval in the task description. Otherwise, you will receive tons of request/emails asking when will you release more qualification/HITs.
2.	No need to have many workers. 
Hire a small group & get familiar with each workers & only hire best workers. 

Why?
-	Based on my experience, 6 workers can finish 1000 HITs in one week. 9 workers can finish 1000 in 3 days. 
-	Small group is better because the workers would not finish HITs in a hurry. Otherwise, they always worry about when will the batch ends. 
-	Small group is better because you get time to "educate" each worker until they work well. Then you do not need to inspect every result and fully trust your worker. 
-	Control the quality of workers are much more effective than controlling the quality of HITs.

3.	Qualification: Approval rate > 95% or even 99%. I did my task with 95% and find that lots of workers have an approval rate>99%. Set it higher and you will feel easier and save much time…
4.	Trick: 
-	AMTurk doesn’t offer contact info of workers….
You can send an "invitation qualification” only to workers who emailed you…
That means, only people email you can work on your HITs.
It is super useful to have workers’ email and communicate with them…and they can ask you question if they are not certain about their results
5.	Be selective when hiring workers! Be generous when approving the HITs! I didn’t reject any HITs…
6.	Be aware of how your interface show in different browsers, e.g., image rotation
7.	You can create a document collecting workers frequently asked questions and include tricky examples. Then forward the document to your workers. That also helps because you cannot include that much examples in your website’s instructions.
8.	Instructions and guidance are always biased, computer vision is biased. 
9.	Qualification & exam is important! Performance increases after qualification and exam.
I set qualification to teach workers the basic ideas of our task. During qualification, workers get notice whether they do correctly or incorrectly for each step and why.
I set exam to examine their performance
10.	How to write a description of the task, see other requester’s description, such as Qi Zhao. 
11.	Write the instructions in "normal people"'s language
12.	I also think each student in Computer Vision should collect dataset at least once by any chance.
13.	Don’t be panic if you find all your hits disappear, the reason could be: (1) all your HITs are taken by workers in a second! They use script to automatically accept tasks :（2）Your HITs reach the expiration date…You can update the expiration date via boto3.






.. note::

   This project is under active development.

Contents
--------

.. toctree::

   usage
   Boto3
   api
