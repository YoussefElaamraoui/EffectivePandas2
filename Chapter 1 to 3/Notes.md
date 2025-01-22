## Chapter 1-2-3 : Introduction

Some of the concepts I found usefull to know or new to my knowledge

> **Whats a REPL?**

**REPL** stands for **Read-Eval-Print Loop**. It is an interactive programming environment that processes one command at a time.
> 

### Usefull commands

Jupyter notebook has two modes, the code mode and the edit one, the first one is to change your code the second one you can use the shortcut commands, which are enabled by pressing enter when you are inside a cell then you can use the commands you want 

```python
h : show keyboard shortcuts
a : Inserts a new cell above teh current cell
b : Inserts a new cell belowe the current cell
x : Cuts the current cell
c : copies current cell
m : from code to markdown
```

### Line magic & cell magic

```python
#line magic %
#cell magic %%
#Both special commands, the first is just a line, the second is the complete cell
#which has a "special command"

#For instance, it will check of much time it takes to run the code 
%timeit x = range (5)
```

### Exercises

***1 ) Difference between jupyternotebook and lab?*** 

The first is the jupyter notebook as we know it the second one is the version that has more tools, like UI visualization some more interactive features and so forth 

***2)Creation and running a new line in Jupyternotebook?***

You can create it with the graphics, or you can use the shortcut with the commands,and to run you can just use shift and enter 

***3) From code to markdown how can you do it ?***

By using the command m, you can change it from code to markdown

***4) How can you save your work in jupyter notebook?***

It does it automatically or you can just do the ctrl+save, or the save icon 

***5)What happens when you interrupt a kernel in jupyter notebook***

**Running Code Stops**: Any currently executing code (e.g., loops, long-running computations) is stopped immediately.

**Current State Preserved**: The variables and outputs that have already been defined remain in memory, so you don’t lose progress unless you restart the kernel.

***6)how do you restart the kernel in jupyternotebook?***

**Using the Toolbar**:

Go to the menu bar, select **Kernel**, and click **Restart Kernel**.

**Using a Shortcut**: Press 0 0 (zero twice quickly).