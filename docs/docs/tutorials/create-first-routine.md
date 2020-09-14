---
layout: page
section: docs
title: Create and modify a method in SkookumScript
numbered-headers: true
footer: false
sharing: false
date: 2017-07-12

---

_SkookumScript Intro Tutorial 1_{:.hdr}

<div markdown="1" class="note">

**Prerequisites**{:.hdr}

This page assumes that you have already done these three things:

[![SkookumScript + Unreal](/images/Unreal/SkookumAndUnreal_trans.png){:.pull-right .height6em}](/docs/ue4/setup/)
1) [Installed Unreal Engine 4.](https://docs.unrealengine.com/latest/INT/GettingStarted/Installation/)<br />
2) [Installed the SkookumScript Unreal Engine 4 Plugin.](/docs/ue4/setup/)<br />
3) [Set up a new or pre-existing UE4 project to use SkookumScript.](/docs/ue4/setup-sk-proj/)

Ensure that either the SkookumIDE and UE4 Editor are running before continuing.
</div>

## Adding custom routines to a project

SkookumScript can easily be used to execute pre-existing generic engine commands while your project is running. Eventually though, you will want to add custom SkookumScript behavior to your project such as adding _methods_ which are a type of [routine](/docs/v3.0/lang/invocations/routines/).

For this tutorial, we will create and modify a SkookumScript routine that solves the classic [FizzBuzz Problem](https://rosettacode.org/wiki/FizzBuzz):

<div markdown="1" class="focus">

### The FizzBuzz Problem

Write a program that prints the integers from 1 to 100 (inclusive). But:

- For multiples of three, print `Fizz` instead of the number.
- for multiples of five, print `Buzz` instead of the number.
- for multiples of both three and five, print `FizzBuzz` instead of the number.
</div>

Let's get started!


### Create a method

1. In the [**Classes** widget](/docs/v3.0/ide/classes/), select `Master`, which is a subclass of `Mind`. (To easily locate it, type **Master** into the search box.) This is the class to which you would like to add your new routine. 

2. At the bottom of the [**Members** widget](/docs/v3.0/ide/members/), open the [**New Class or Member** pane](/docs/v3.0/ide/new/) by clicking **New Class or Member**.

3. In the **Name** box, enter **fizz_buzz**—this is the name of our new method. 

4. Use the **instance/class (i/c)** drop-down list box to specify **i**—this means that new method will be an _instance method_ rather than a _class method_ (**c**). 

5. Use the **Overlay** drop-down list box to specify the [overlay] your new method will be added to. If you are running the SkookumIDE and UE4 Editor, select the **Project** overlay. If you are running the standalone SkookumDemo, select the **SkookumDemo** overlay.

6. Click **Add**. Voila, you have created a method!

![Adding Master.fizz_buzz()](/images/Docs/Tut1-SkIDE-new.png){:.img-center}

Adding an instance method named  `fizz_buzz` to the `Master` class in the `Project` overlay.
{:.caption}

*TIP*{: .tip} The `Master` class is a good starting point to add initial code for most projects.

The **New Class or Member** pane may be small, but it is a powerhouse of creation. Learn more about its amazing abilities [here](/docs/v3.0/ide/new/).
{:.aside}


### Add a method body

When you create a method, the default text for a new method will appear in an **Editor** widget:

![An Editor widget displaying the default method text](/images/Docs/SkIDE-Editor-defaultmethod.jpg){:.pic-full}

An **Editor** widget displaying the default method text.
{:.caption}

Now we'll update the comments and code body to add a method that solves the FizzBuzz problem. Delete the default text and replace it with the following:

{% highlight js linenos %}
//-------------------------------------------------
// A SkookumScript solution to the FizzBuzz Problem    
//-------------------------------------------------

() 
  [
  1.to 100
    [
    println(
      if idx.mod(15) = 0 ["FizzBuzz"]
        idx.mod(3) = 0   ["Fizz"]
        idx.mod(5) = 0   ["Buzz"]
        else             [idx])
    ]
  ]
{% endhighlight %}

For more ways to solve the FizzBuzz problem with SkookumScript, see more [SkookumScript FizzBuzz examples on RosettaCode](https://rosettacode.org/wiki/FizzBuzz#SkookumScript).
{:.aside}


### Commit a method to the runtime

Now that we have added our FizzBuzz solution to our `fizz_buzz` method, we will compile it and send it to the project runtime. To do this, do any of the following using the SkookumIDE: 

- On the **Build** menu, select **Commit**.
- On the toolbar, click the **Commit** (gears with a question mark) button.
- Press F7.

If the compiling is successful—and it will be, if you copied the example code into the **Editor** widget properly—the question mark on the **Commit** button will become a green check mark and the method will be committed to the runtime.

![Commit button before](/images/Docs/Tut1-SkIDE-commit1.png){:.img-center} | ![Commit button after](/images/Docs/Tut1-SkIDE-commit2.png){:.img-center}
{:.whole}

Before compiling and committing changes, the **Commit** button has a question mark. After compiling and committing changes, the **Commit** button has a green check mark.
{:.caption}


### Execute a method

Now we will execute our new `fizz_buzz` method in our running project:

1. Ensure that your project is running. (To run your project, in the Unreal Editor toolbar click the **Play** button or press Alt+P.) 

2. In the [**Workbench (REPL)** widget](/docs/v3.0/ide/workbench/), enter **fizz_buzz** on any blank line. 

3. Ensure that the caret is on that line and press F4 to execute it.

You should see this output in the [**Log** widget](/docs/v3.0/ide/log/):

```text
1
2
Fizz
4
Buzz
Fizz
7
8
Fizz
11
Buzz
Fizz
13
14
FizzBuzz
17
16
Fizz
19
Buzz
Fizz
```

...and so on, until...

```text
91
92
Fizz
94
Buzz
Fizz
97
98
Fizz
Buzz

nil
```

*NOTE*{: .mark} The `nil` at the end is the result of the call to the `fizz_buzz` method, which returns nothing.

Congratulations! You have made and executed a simple method.

*TIP*{: .tip} Routines such as `fizz_buzz()` can be run as many times as you like from the Workbench like this, or you can call them in other routines that you write.


### Modify a method

To specify different parameters or the code body of a method you just change the empty parameters `()` and the rest of the code as needed and then recommit the changes.

Our `fizz_buzz` method currently does 100 iterations (internal repetitions), one for each integer from 1 to 100. Now we'll modify it so we can specify the number of iterations as an argument when we execute it from the **Workbench (REPL)** widget. 

1. In the **Editor** widget, replace the code for the `fizz_buzz` method with this: 

{% highlight js linenos %}
//---------------------------------------------------
// SkookumScript FizzBuzz with specifiable parameters     
//---------------------------------------------------

(Integer count: 100) 
  [
  1.to count
    [
    println(
      if idx.mod(15) = 0 ["FizzBuzz"]
        idx.mod(3) = 0   ["Fizz"]
        idx.mod(5) = 0   ["Buzz"]
        else             [idx])
    ]
  ]
{% endhighlight %}

{:start="2"}
2. [Compile and commit](#commit-a-method-to-the-runtime) the revised method.

Now you can call `fizz_buzz` with a specific number of iterations:

{% highlight js linenos %}
// Call with 50 iterations
fizz_buzz(50)

// Call with default 100 iterations
fizz_buzz
{% endhighlight %}

*TIP*{: .tip} Committing changes live while a project is using routines that are changed, will automatically use the updated versions of the routines the next time they are called without needing to stop the runtime—which is very cool.


## Experiment and add more routines

We recommend experimenting with this FizzBuzz example or make new methods and see what changes you can make.

<div markdown="1" class="aside">
*TIP*{: .tip} Parameters are [described in detail in the syntax](/docs/v3.0/lang/syntax/#parameters).

Look around at other routines in the class hierarchy using the SkookumIDE **Classes** and **Members** widgets to get ideas.

*NOTE*{:.mark} Routines that have no code block body `[ ]` are defined and written in C++, though you will still see their parameters and description comments.
</div>

_If you have questions or comments about this tutorial, please post them to the [SkookumScript Forum page for this tutorial](https://skookum.chat/t/create-your-first-routine-in-a-new-project/1169)._


---
[**Next >>**{:.tip} **SkookumScript UE4 Plugin Basic Tutorial 1: Create and rotate a cube Blueprint**](/docs/tutorials/create-rotate-cube/)<br/>
[**<< Previous**{:.tip} **Tutorials table of contents**](/docs/tutorials/)
{:.bubble-link}


[overlay]: /docs/v3.0/lang/layout/overlays/