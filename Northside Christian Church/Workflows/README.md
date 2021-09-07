## Workflows

1. Import all the workflows in this repo. There are quite a few, but the only one to really pay attention to is the primary _Online Baptism Class_ workflow. The name indicates which version includes Wistia functionality and which does not.

2. Each workflow will have one or more attributes where the description starts with _CHANGE_, that indicates you need to change what the attribute's default value is. The description / name  indicates what it should be changed to.

3. Several workflows send emails that aren't System Communications because of the complex lava within the body. Check the following workflows for a single action in each to update the email content to match your organization's branding / communication style:

    1. HELPER: Process Individual Incomplete Week 1 Reminder
    2. HELPER: Process Individual Incomplete Week 2 Reminder
    3. HELPER: Process Individual Incomplete Week 3 Reminder
    4. HELPER: Process Individual Not Started Week 1 Reminder
    5. HELPER: Process Individual Not Started Week 2 Reminder
    6. HELPER: Process Individual Not Started Week 3 Reminder
    7. Baptism Class - Email requestor when connection is created

4. Several workflows send System Communications, so those workflow actions need to be set to the correct System Communication.

    1. Online Baptism Class
        1. Activity: Prepare for Next Step > Action: Send Email to Person Who Completed Class
            - Email to set: _Connection - Completed Baptism Class_
        2. Activity: Not Ready Yet > Action: Send Not Ready Yet Email
            - Email to set: _Connection - Not Ready for Baptism_
    2. Send Final Baptism Class Email if "Not Ready"
        1. Activity: Start, Action: Send email to the requestor
        2. Email to set: _Baptism - Not Ready Yet Final Follow-Up_

That's all with workflows! Head back to the main README.md for the remaining instructions on setup!
