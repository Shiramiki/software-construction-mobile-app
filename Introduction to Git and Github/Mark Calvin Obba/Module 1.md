## Course Introduction
From this lesson, I learned that the course is about version control systems, which help keep track of different versions of code and configuration files. These tools aren’t just for programmers—they’re useful for anyone in IT because they make it easier to track changes, fix mistakes and work with others.
The course mainly focuses on Git and GitHub. Git helps manage the history of code, while GitHub allows that code to be stored online and shared with others. By the end of the course, I should be able to use Git to manage my work, collaborate with others on GitHub, and build a GitHub portfolio, which is important when applying for IT jobs.
The instructor explained how version control is used in real projects, especially when many people are working on the same system. Git helps teams stay organized, avoid conflicts and recover from errors. He also shared his personal journey in tech and emphasized the importance of sharing knowledge and helping others succeed.
The course will cover both basic and advanced Git features, like branching and merging, and show how Git can be useful in real situations such as debugging or emergencies. To follow along, I’ll need Git, Python 3 and some basic Linux command line knowledge. Some topics may be challenging at first, but with practice and review, they’ll make more sense.
Overall, the course is meant to build a strong foundation in Git and version control and help me use these tools confidently in real IT work.


## Intro to Module 1: Version Control
I learned that working in IT involves managing many files that change over time, such as scripts and configuration settings. Because of these changes, it’s important to keep a clear record of what was modified and why so issues can be traced and fixed easily.
Version control helps with troubleshooting, reduces human error, and allows teams to roll back to a stable version instead of pushing rushed fixes. The lesson showed how mistakes can happen when changes aren’t properly tested and how rolling back can save time and prevent bigger problems.
I understood that version control systems like Git are essential for keeping systems stable, supporting collaboration and managing changes in a professional IT environment.

## Keeping Historical Copies
This lesson explained that many people have already used a basic form of version control without realizing it. For example making copies of files, saving different versions or emailing work back and forth when working in a team. These methods help in case you need to go back to an earlier version or restore something that was removed.
However, this approach is considered primitive because it is manual and inefficient. You have to remember to make copies you often duplicate entire projects even when only small changes are made and it’s hard to track who made a change or why it was done.
The main idea behind version control is still the same: keeping track of changes over time. Version control systems like Git do this in a much better and more organized way. They allow you to track changes to different types of files, collaborate with others and revert changes when needed.
I also understood that Git is essentially a smarter and more reliable way of managing historical versions of a project and comparing changes made over time.

## Review Diffing files
 Some code snippits showing the difference of code before and after editiing/change.
Code for Diffing files
cat rearrange1.py 
Code output:


#!/usr/bin/env python3

import re

def rearrange_name(name):

    result = re.search(r"^([\w .]*), ([\w .]*)$", name)

    if result == None:

        return name

    return "{} {}".format(result[2], result[1])

user@ubuntu:~$ cat rearrange2.py 

#!/usr/bin/env python3

import re

def rearrange_name(name):

    result = re.search(r"^([\w .-]*), ([\w .-]*)$", name)

    if result == None:

        return name


    return "{} {}".format(result[2], result[1])


Code for diffing files 2:
cat rearrange2.py 

Code output:

#!/usr/bin/env python3

import re

def rearrange_name(name):

    result = re.search(r"^([\w .-]*), ([\w .-]*)$", name)

    if result == None:

        return name

    return "{} {}".format(result[2], result[1])

Code for diffing files 3:
diff rearrange1.py rearrange2.py 

Code output:

6c6

<     result = re.search(r"^([\w .]*), ([\w .]*)$", name)

---

>     result = re.search(r"^([\w .-]*), ([\w .-]*)$", name)
 Code for diffing file 4:
diff validations1.py validations2.py 
Code output:

5c5,6

<	assert (type(username) == str), "username must be a string"

--

>	if type(username != str: 

> 	    raise TypeError("username must be a string"

11a13,15

>	    return False

>	# Usernames can't begin with a number

>	if username[0].isnumeric():

 code for diffing files:
diff -u validations1.py validations2.py 
Code output:

--- validations1.py	2019-06-06 14:28:49.639209499 +0200

+++ validations2.py	2019-06-06 14:30:48.019360890 +0200

@@ -2,7 +2,8 @@

 

 

 def validate_user(username, minlen):

-    assert type(username) == str, "username must be a string"

+    if type(username) != str:

+        raise TypeError("username must be a string")

     if minlen < 1:

         raise ValueError("minlen must be at least 1")

     

@@ -10,5 +11,8 @@

         return False

     if not username.isalnum():

         return False

+    #Usernames can't begin with a number

+    if username[0].isnumeric():

+        return False

     return True


## diffing File
# Understanding Code Differences with `diff`
I learnt how to quickly and reliably spot changes between two versions of code —without straining your eyes!

diff -u rearrange1.py rearrange2.py
There are a lot of tools out there to compare files. Diff is the most popular one, but not the only one available. For example, wdiff highlights the words that have changed in a file instead of working line by line like diff does
meld rearrange1.py rearrange2.py
# or
kdiff3 rearrange1.py rearrange2.py
# or (inside vim)
vim -d rearrange1.py rearrange2.py

## Applying Changes
