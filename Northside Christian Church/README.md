# How to Rock Your Online Courses

## Start Here
So whether you're here to learn or to plug-and-play this course into your own organization, we've got you covered. You can find everything you need in this repo! And if you have any questions or run into any snags, hit me up on Rocket.chat **@leahjennings**.

### Components to Setup
1. Connection Opportunities
2. Steps
3. System Communications
4. Person Attributes
5. Workflows
6. Triggers & Jobs


### Connection Opportunities
We'll be creating two opportunities, Online Baptism Class and Baptism Conversations.

### 1. Online Baptism Class
Create a new Connection Opportunity with the following settings:

1. Name: _Online Baptism Class_
2. Icon CSS Class: _fab fa-leanpub_
3. Connection Request Attributes: leave at default
3. Placement Groups: leave at default
3. Connector Groups: leave at default
3. Workflows: leave at default
3. Advanced Settings: leave at default

### 2. Baptism Conversations

Create a new Connection Opportunity with the following settings:

1. Name: _Baptism Conversations_
2. Icon CSS Class: _fa fa-tint_
3. Connection Request Attributes: leave at default
3. Placement Groups: leave at default
3. Connector Groups: set to a group and set a default connector _(should be someone from your Next Steps Team or whoever would be the staff member who is facilitating baptism conversations)_
3. Workflows: leave at default
3. Advanced Settings: leave at default

***

### Steps
We're going to create a new Step Program called _Baptism Class_.

1. Icon CSS Class: _fas fa-tint_
2. Statuses
    1. Enrolled (Is Complete: _true_)
    2. Finished (Is Complete: _true_)
    3. In Progress (Is Complete: _false_)
3. Workflows: none

Step Types:
1. Enrolled
    1. Icon CSS Class (_fas fa-play-circle_)
    2. Allow Multiple (_true_)
    3. Spans Time (_false_)
    4. Is Date Required (_true_)
    5. No Step Attributes or Workflows
2. Video #1
    1. Icon CSS Class (_fas fa-film_)
    2. Allow Multiple (_true_)
    3. Spans Time (_true_)
    4. Is Date Required (_true_)
    5. Prerequisite Steps Enabled (_Enrolled_)
    6. No Step Attributes or Workflows
3. Video #2
    1. Icon CSS Class (_fas fa-film_)
    2. Allow Multiple (_true_)
    3. Spans Time (_true_)
    4. Is Date Required (_true_)
    5. Prerequisite Steps Enabled (_Enrolled_, _Video #1_)
    6. No Step Attributes or Workflows
4. Video #3
    1. Icon CSS Class (_fas fa-film_)
    2. Allow Multiple (_true_)
    3. Spans Time (_true_)
    4. Is Date Required (_true_)
    5. Prerequisite Steps Enabled (_Enrolled_, _Video #1_, _Video #2_)
    6. No Step Attributes or Workflows

***

### System Communications
You'll need to create 3 different emails (the code for each of them is in the System Communications folder):
- _Baptism - Not Ready Yet Final Follow-Up_
- _Connection - Completed Baptism Class_
- _Connection - Not Ready for Baptism_

Once setup, you'll want to change the branding/styling and verbiage, but leave any buttons pointing to workflows.

***

### Person Attributes
We added these before we had Steps, so you can add these so the workflow will know which attributes to update, OR you can delete the workflow actions in the Online Baptism Class workflow that set these attributes. But essentially we need three attributes that are all a `Date` field type:

1. Baptism Video #1 Completion Date (Key: _BaptismVideo1CompletionDate_)
2. Baptism Video #2 Completion Date (Key: _BaptismVideo2CompletionDate_)
3. Baptism Video #3 Completion Date (Key: _BaptismVideo3CompletionDate_)

***

### Workflows
Click into the Workflows folder above to see more details on those, then come back to complete the rest of the steps.

***

### Triggers & Jobs
Now that the workflows are imported, we can setup the different triggers and jobs that are needed to make all of this work together.

### Triggers
1. Trigger on Connection Request Created
    1. Go to the settings of the Online Baptism Class connection opportunity
    2. Expand Workflows and add a new Workflow Type
    3. Choose _Baptism Class - Email requestor when connection is created_ and trigger it on _Request Started_
2. Trigger on Connect Request Future Follow-Up Reached
    1. Go to the settings of the Online Baptism Class connection opportunity
    2. Expand Workflows and add a new Workflow Type
    3. Choose _Send Final Baptism Class Email if "Not Ready"_ and trigger it on _Future Followup Date Reached_

### Jobs
We'll create two new jobs, one to process "Incomplete Baptism Courses" and one to process "Not Started Baptism Courses"

1. Incomplete Baptism Courses
    1. Name: _Process Incomplete Baptism Classes_
    2. Job Type: _Launch Workflow_
    3. Workflow: _Process All Incomplete Classes_
    4. Cron Expression: _0 0 9 1/1 * ? *_
2. Not Started Baptism Courses
    1. Name: _Process Not Started Baptism Classes_
    2. Job Type: _Launch Workflow_
    3. Workflow: _Process All Not Started Classes_
    4. Cron Expression: _0 0 9 1/1 * ? *_

***

### Wrapping it Up
The last piece of the puzzle is setting a Workflow Type Id in one of the System Communications.

1. Open the _Baptism - Not Ready Yet Final Follow-Up_ System Communication
2. Switch to the code / Advanced view
3. The very first line of the communication needs to be updated so that the worfklow type Id (which is going to be imported in the code as 192) needs to be updated to whatever the workflow type id is on your instance for the _Ready to Talk About Baptism_ workflow

And that's it! To start the course, run the enrollment workflow and watch the pieces work together.
