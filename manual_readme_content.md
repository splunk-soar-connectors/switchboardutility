
----------------------------------------------------------------------------------------------------

----------------------------------------------------------------------------------------------------

Switchboard is an app designed to make executing the appropriate playbooks easier.  
  
The process for this execution depends on two things:

-   One active playbook that contains the switchboard **run playbooks** action
-   Specifically named playbooks to match on

Executing the **run playbooks** accepts 3 inputs for playbook matching:

-   Repository name - (Required) Indicates which repository to match playbooks from
-   Product name - Accepts a string that represents the rule that generated the event
-   Rule name - Accepts a comma seperated string of product names to match on

Types of named playbooks:

1.  Rule: &ltexact rule name to match>
    -   Matches if the literal rule name passed into **run playbooks** is the same
2.  Product: &ltexact product name to match>
    -   Matches if the playbook product name is a substring of the product name passed into **run
        playbooks**
3.  Subject: &ltsubstring to partially match against the rule name text>
    -   Matches if the subject string is a substring of the rule name passed to **run playbooks**
4.  Field: &ltexact field name to match>
    -   Matches if the playbook's specified field name is in the original artifact in the container

Once the set of matching playbooks is determined, those matching playbooks will be executed  
  
The matching playbooks and total count of executed playbooks are outputs of the action  
  
If no playbooks matched, no further playbooks will be executed by **run playbooks**

----------------------------------------------------------------------------------------------------

----------------------------------------------------------------------------------------------------
