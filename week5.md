# Week 5 Lab Report

## Exploring Grep
<br>


Today I will be exploring three interesting command-line options for the "grep" command.

<br>

First, let's see a standard way to use grep. I will be using the "technical" directory and a file called "find-results.txt" (which is full of text from technical) to demonstrate. 

Below is an example of using grep to find all lines in the find-results.txt that contain "report".

```
grep "report" find-results.txt

technical/government/About_LSC/Progress_report.txt
technical/government/About_LSC/Strategic_report.txt
technical/government/About_LSC/Special_report_to_congress.txt
technical/government/About_LSC/commission_report.txt
technical/government/About_LSC/reporting_system.txt
technical/911report
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-3.txt
technical/911report/chapter-2.txt
technical/911report/chapter-1.txt
technical/911report/chapter-5.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-9.txt
technical/911report/chapter-8.txt
technical/911report/preface.txt
technical/911report/chapter-12.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
```

The above output is produced in terminal. Every line from the file find-results.txt that contains the word "report" is printed.

However, grep is case sensitive. This brings me to my first command line option for grep:

`grep -i`

<br>


## Exploring grep -i
<br>

We can use grep -i to ignore upper vs. lower case. If I used the commmand

`grep -i "report" find-results.txt`

The output below is produced:

```
technical/government/About_LSC/Progress_report.txt
technical/government/About_LSC/Strategic_report.txt
technical/government/About_LSC/Special_report_to_congress.txt
technical/government/About_LSC/commission_report.txt
technical/government/About_LSC/reporting_system.txt
technical/government/About_LSC/State_Planning_Report.txt
technical/government/About_LSC/State_Planning_Special_Report.txt
technical/government/Post_Rate_Comm/ReportToCongress2002WEB.txt
technical/911report
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-3.txt
technical/911report/chapter-2.txt
technical/911report/chapter-1.txt
technical/911report/chapter-5.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-9.txt
technical/911report/chapter-8.txt
technical/911report/preface.txt
technical/911report/chapter-12.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
```

As we can see, all lines containing "report" and/or "Report" are printed in the terminal.




In this example, we can see that the casing of the first letter in "report" is not taken into account. How about the casing of the letters following the first?

In find-results.txt, I will add this line: “technical/911rEpOrT/chapter-12.txt” Here we can see that the casing is mixed up throughout the word. I will run grep -i "report" find-results.txt again to test this out. 

```
grep -i "report" find-results.txt

technical/government/About_LSC/Progress_report.txt
technical/government/About_LSC/Strategic_report.txt
technical/government/About_LSC/Special_report_to_congress.txt
technical/government/About_LSC/commission_report.txt
technical/government/About_LSC/reporting_system.txt
technical/government/About_LSC/State_Planning_Report.txt
technical/government/About_LSC/State_Planning_Special_Report.txt
technical/government/Post_Rate_Comm/ReportToCongress2002WEB.txt
technical/911report
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-3.txt
technical/911report/chapter-2.txt
technical/911report/chapter-1.txt
technical/911report/chapter-5.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-9.txt
technical/911report/chapter-8.txt
technical/911report/preface.txt
technical/911report/chapter-12.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
technical/911rEpOrT/chapter-12.txt
```

It turns out that the output is the same as before but it also includes the new line that I added in find-results.txt. Therefore, we can conclude that grep -i ignores the casing for ALL letters in the word. 

<br>

What about if there is a space between the letters? I’m going to add this line 
technical/911r_EpOrT/chapter-13.txt which has an underscore between r and E. Let’s see how it runs using grep -i "report" find-results.txt.

```
grep -i "report" find-results.txt

technical/government/About_LSC/Progress_report.txt
technical/government/About_LSC/Strategic_report.txt
technical/government/About_LSC/Special_report_to_congress.txt
technical/government/About_LSC/commission_report.txt
technical/government/About_LSC/reporting_system.txt
technical/government/About_LSC/State_Planning_Report.txt
technical/government/About_LSC/State_Planning_Special_Report.txt
technical/government/Post_Rate_Comm/ReportToCongress2002WEB.txt
technical/911report
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-3.txt
technical/911report/chapter-2.txt
technical/911report/chapter-1.txt
technical/911report/chapter-5.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-9.txt
technical/911report/chapter-8.txt
technical/911report/preface.txt
technical/911report/chapter-12.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
technical/911rEpOrT/chapter-12.txt
```
Looks like since an underscore separates the characters, it will not be a part of the output! Therefore, with or without -i, spacing/underscores are evaluated before the output is produced.

<br>


## Exploring grep --color=[when]
<br>

The next command line option I will be using is “--color=[when]”. When using -–color, we have to specify the word we are looking for.  The output will include all lines in the file containing the word, and will color the specified word in the terminal. We also see a portion of the command called “when”, which can store either “never”, “always” or “auto”. I will explore all three of these different values for “when”. 


Let’s say I want to find the line containing “preface” using grep. I also want to highlight the word “preface” in my output.  I can use the command:

`grep --color=always preface find-results.txt`

The command works as follows:
```
grep --color=always preface find-results.txt
technical/911report/preface.txt
```

**NOTE: the above code block doesn't show color. The actual output would look like this: 

grep --color=always <span style="color:red"> preface </span> find-results.txt
technical/911report/preface.txt


As we can see, find-results.txt has one lining containing the word “preface” and so it printed out this line and highlighted “preface” in red. This is useful for readability, when you are looking through even larger quantities of data. In this example, I used “always” because it colors the matching string.

<br>

What if I used “auto” instead of “always”? I will run the command 

`grep --color=auto preface find-results.txt`

for the following output:

```
grep --color=auto preface find-results.txt

technical/911report/preface.txt
```

Once again, the actual output will have color as follows: 

grep --color=always <span style="color:red"> preface </span> find-results.txt
technical/911report/preface.txt

We see that the result is actually the same. So what is the difference between “always” and “auto”?  Auto will display color in the output unless the output is piped to another command or redirected to a file, while always will always display color. 

<br>

What about using “never”?
grep --color=never preface find-results.txt 

```
grep --color=never preface find-results.txt 

technical/911report/preface.txt
```
Here we can see that the output is not colored. Now, I don’t see how this is particularly useful since you can get the same output without including “--color=never” in the command. Nevertheless, the option is available. 



<br>


## Exploring grep -e
<br>

The final command line option I’ll be exploring is grep “-e”. This specifies a pattern used during the search of the input. 

`grep -e '1471' find-results.txt`

We get:

```
grep -e '1471' find-results.txt 
technical/biomed/1471-2350-4-3.txt
technical/biomed/1471-2156-2-3.txt
technical/biomed/1471-2156-3-11.txt
technical/biomed/1471-2121-3-10.txt
technical/biomed/1471-2172-3-4.txt
technical/biomed/1471-2466-1-1.txt

...

technical/biomed/1471-2210-1-3.txt
technical/biomed/1471-2334-1-13.txt
technical/biomed/1471-2407-3-16.txt
technical/biomed/1471-2164-4-2.txt
technical/biomed/1471-2105-3-4.txt
technical/biomed/1471-2121-3-21.txt
technical/biomed/1471-2202-4-2.txt
technical/biomed/1471-2172-3-9.txt
technical/biomed/1471-2199-2-6.txt
technical/biomed/1471-2121-2-3.txt
technical/biomed/1471-213X-1-11.txt
```
**NOTE: I ommitted several lines of the output in the middle to save space, since the output is very long!

This command uses ‘ ’ instead of “ ” for the specified pattern. Looking at the output, we see all lines containing 1471 printed out. However, what is useful about this instead of just using ordinary “grep”? 

<br>


A useful aspect of -e is the fact that we can actually use it multiple times in the same line! For example, I can use the command 

`grep -e 'Office' -e 'Media' find-results.txt`

```
grep -e 'Office' -e 'Media' find-results.txt

technical/government/Gen_Account_Office
technical/government/Gen_Account_Office/d0269g.txt
technical/government/Gen_Account_Office/Testimony_cg00010t.txt
technical/government/Gen_Account_Office/og97032.txt
technical/government/Gen_Account_Office/og99036.txt
technical/government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
technical/government/Gen_Account_Office/Sept27-2002_d02966.txt

...

technical/government/Media/Barr_sharpening_ax.txt
technical/government/Media/Legal_Aid_attorney.txt
technical/government/Media/The_Bend_Bulletin.txt
technical/government/Media/Legal_services_for_poor.txt
technical/government/Media/Farm_workers.txt
technical/government/Media/Entities_Merge.txt
technical/government/Media/less_legal_aid.txt
technical/government/Media/Understanding.txt
technical/government/Media/Do-it-yourself_divorce.txt
technical/government/Media/Politician_Practices.txt
technical/government/Media/defend_yourself.txt
technical/government/Media/Towson_Attorney.txt
technical/government/Media/Pro-bono_road_show.txt
technical/government/Media/A_Perk_of_Age.txt
technical/government/Media/A_helping_hand.txt
technical/government/Media/pro_bono_efforts.txt
technical/government/Media/5_Legal_Groups.txt
technical/government/Media/Greedy_Generous.txt
technical/government/Media/Retirement_Has_Its_Appeal.txt
technical/government/Media/RoanokeTimes.txt
technical/government/Media/NJ_Legal_Services.txt
technical/government/Media/Bridging_legal_aid_gap.txt
technical/government/Media/Legal_Aid_campaign.txt
technical/government/Media/Aid_Gets_7_Million.txt
```

Once again, I ommitted part of the output for spacial purposes. The output includes all lines with either 'Office' or 'Media' or both. 

<br>

It is also important to note what happens when we run a command that is expected to produce an error. For example, let’s say I want to find a line containing my name, “Kaleigh”. However, there shouldn’t be a line with my name in find-results.txt. Let’s see how the program responds when I run the command 

`grep -e 'Kaleigh' find-results.txt`

![](W5%20SS/Screen%20Shot%202022-10-30%20at%206.02.12%20PM.png)

We see that the command did not produce an output, and indicates that something went wrong with the red dot on the left.  This functionality is actually rather reasonable, since we don’t want anything to be printed if it's not there. 
