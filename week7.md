# Week 7 Lab Report

## Part 1: Changing the name of the start parameter and its uses to base
<br>

The vim task that I will be focusing on in this lab report is changing the name of the ``start`` parameter of ``getFiles`` and all of its uses to instead be called ``base``. These changes will take place in the ``DocSearchServer.java`` file.

<br>

The original code for ``DocSearchServer.java`` in VSCode is as below:
![Alt text](W7%20SS/original%20code.png)


To edit with vim, type ``vim DocSearchServer.java``. 

<br>

Now, we will start counting the keystrokes to finish the edit. 

``/`` ``s`` ``t`` ``a`` ``r`` ``t`` 

``<return>``

![Alt text](W7%20SS/start.png)

The ``/start`` command + ``<return>`` will take the cursor to the first occurrence of start. 

<br>

``c`` ``e``
![Alt text](W7%20SS/ce.png)

Typing ``c`` and ``e`` will delete the word ``start`` and enter insert mode. 

<br>

``b`` ``a`` ``s`` ``e``

![Alt text](W7%20SS/base.png)

This command inserts the word ``base`` where the cursor is. 

<br>

``<esc>``

![Alt text](W7%20SS/esc.png)

Pressing ``<esc>`` exits insert mode and goes back to normal mode. 

<br>

``n``

![Alt text](W7%20SS/n.png)

This takes us to the next instance of ``start``.

<br>

``.``
![Alt text](W7%20SS/period.png)

The period will repeat the previous sequence of commands, which was ``c`` ``e`` and ``base``.


<br>

``n``
![Alt text](W7%20SS/n2.png)

Since there is one more instance of ``start`` in the file, we use ``n`` one more time to arrive at the last occurrence of ``start``.

<br>

``.``
![Alt text](W7%20SS/per2.png)
This repeats the previous sequence, which was ``c`` ``e`` and ``base``.

<br>

Finally, we have to save and quit.

``:wq``

![Alt text](W7%20SS/saveandexit.png)
``:wq`` saves the file and exits vim.

<br>

Our new file looks like this in VSCode:

![Alt text](W7%20SS/new.png)

The total number of keystrokes was 21. 

## Part 2: Style
<br>

Style 1: Took me 1 minute and 13 seconds. I typed the scp command incorrectly a few times because of the “:~/” at the end.

Style 2: Took me 35 seconds and I didn’t encounter any issues. 
<br>


Reflection:

For this scenario, I preferred using the second style because it was much faster and easier. As long as the correct commands are known in Vim, the task can be finished smoothly. I think for a more complex task it could be more difficult though. At least personally, my knowledge of Vim is new and still growing. Therefore, for now it is probably easier for me to do complex problems on the remote server using VSCode and scp. 
