[comment]: # "Auto-generated SOAR connector documentation"
# Switchboard

Publisher: Mhike  
Connector Version: 1\.0\.1  
Product Vendor: Mhike  
Product Name: Switchboard  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 4\.9\.0  

The Switchboard app manages various operations used in executing SOAR playbooks


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


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Switchboard asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**https\_port** |  optional  | string | Splunk SOAR HTTPS port if your instance uses one other than 443
**repository\_filter** |  optional  | string | A comma separated list of repositories that shouldn't be added to playbook cache
**cache\_expiration** |  required  | numeric | How long should the playbook cache be valid in seconds
**debug** |  optional  | boolean | Print debugging statements to log

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate connectivity to the Splunk SOAR instance  
[run playbooks](#action-run-playbooks) - Identify and execute matching playbooks  
[on poll](#action-on-poll) - Update the cached playbooks used by switchboard  

## action: 'test connectivity'
Validate connectivity to the Splunk SOAR instance

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'run playbooks'
Identify and execute matching playbooks

Type: **generic**  
Read only: **False**

Based on the standard naming conventions used by the switchboard app, run all matching playbooks in the playbook cache\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**repository\_name** |  required  | The name of the repository to execute playbooks from | string | 
**product\_name** |  optional  | Product strings to match on | string | 
**rule\_name** |  optional  | Rule name to match on | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.product\_name | string | 
action\_result\.parameter\.repository\_name | string | 
action\_result\.parameter\.rule\_name | string | 
action\_result\.data\.\*\.match\_found | boolean | 
action\_result\.data\.\*\.matches | string | 
action\_result\.summary | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'on poll'
Update the cached playbooks used by switchboard

Type: **ingest**  
Read only: **False**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output