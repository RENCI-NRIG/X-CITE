---
title: "Virtual Environments, Containers and Virtualization"
author: ""
date: ""
---

If all software was brilliantly designed and completely free of bugs
then it would be easy to run as many different programs on one machine
as you wanted. All you would need is enough memory and compute power
to run them with. It doesn't look like that's going to happen any time
soon, so we're going to need a way to isolate programs from each other
so they can act like they have their own computer to run on. There are
three basic ways to do this. With ***Virtual Environments*** we'll
configure different programs to run from different places on the
filesystem and to have their own places to load their dependencies
from. With ***Containers*** we'll go a little further: we'll still have
one operating system running many programs, but each program will
appear to get its own filesystem and there won't be any way for the
programs to interfere with each other. Finally, ***Virtualization***
(using ***Virtual Machines*** or ***VMs***) takes a running computer and makes
it look like many such machines, one for each operating system running
on there. There are tradeoffs to each approach.

## Virtual Environments

Let's consider why any of these isolation techniques
matter. Fundamentally, we want software to not be able to interfere
with other programs running on the same computer. At first blush it
would seem like the operating system does that for us. After all, most
of the security measures designed into the OS are there to prevent
unauthorized access, and that includes one program trying to subvert
another one. It doesn't even have to be deliberate. There are plenty
of cases where bugs in programs can affect others.

The problem with just letting the OS handle isolation is that it does
its job just as it was designed. The programs all run separated from
each other and share a common filesystem, network ports, and even some
arcane properties of the OS at its deepest level. And therein lies the
problem: the shared filesystem means that programs will often share
libraries and packages. Ordinarily this is A Good Thing - it saves
disk space and, more importantly, it saves memory. The only is problem
is what to do when you need different versions of the same package.

Suppose you have a Python program called "xraySpectacles.py" and it
uses the package "xrayMath". Suppose you also have a program called
movingChargedParticles.py and it also uses xrayMath. Let's say that,
for reasons lost to time, xraySpectacles requires version 4.04 of
xrayMath. Let's further say that movingChargedParticles requires a
version of xrayMath that is no less than version 10. We now have a
problem. One program or the other is going to fail. If you have the
right version of xrayMath for movingChargedParticles then it will be
the wrong one for xraySpectacles and *vice versa*.

We need a way to have two completely separate Python installations on
the same computer. What we need is a couple of Virtual Environments!
There are two such things in common use. The first, and most common,
is called Anaconda. When you use Anaconda to create a virtual
environment (```conda create```), you'll be prompted for which version of Python to
use. Once the environment is created, you can use the ```conda
install``` command. Any packages you install this way will only be
available to Python programs running under that particular virtual
environment.

You may have noticed that CHESS's JupyterHub uses exactly this kind of
virtual environment. Given that Jupyter is often used as a kind of
"electronic lab notebook", this isolation can be important for
reproducability. If you produced some results under xrayMath 4.01 and
later the package is upgraded to version 4.04, there is no guarantee
you'll get exactly the same results. When this happens, by the way,
the two most common causes are (1) fixing bugs that you had been
unknowingly relying on and (2) handling roundoff errors slightly
differently.

It should also be pointed out that there is another method for creating
virtual environments in Python, and that is ```venv```. Venv is part
of Python so you know it will always be there, wherever you're
working. Venv doesn't have nearly as many features as Anaconda and
it's not as polished, but it has a big feature in it's favor: it's
free software and always will be. Anaconda is commercial and they make
their money charging companies to use their software and their
repository of packages. For a long time they let Universities use it
for free, but in the last couple of months that has changed. People
are still trying to understand what the new licensing terms mean and
whether it affects them or not. It's unfortunate but
understandable. Operating the servers needed to host the repositories
and paying developers to manage the insane complexity of a table of
version dependencies isn't cheap either. On the other hand, if people
graduate having only used venv then future sales of Anaconda will tail
off.

We should take a minute to talk about programs that aren't written in
Python. Virtual Environments are still a valid solution, but in this
case they're done with something a lot more powerful than just
Anaconda. The strategy for any Linux program in general is to
manipulate the contents of the environment variable
```LD_LIBRARY_PATH```. I'm not going to go into any details
here. Suffice it to say the procedure is involved and non-trivial to
troubleshoot if anything goes wrong. Just keep in mind that this
approach exists and is an option if you have your back up against the
wall.

## Containers

Just giving our programs their own libraries and packages might not be
good enough. Suppose our friends xraySpectacles and
movingChargedParticles have had their specific package version
requirements met, but they still bump into each other when they write
to a file called "results.txt". Virtual Environments won't help us
here. What we need is a way to "fool" each program into thinking it
has its own filesystem. And that bit of trickery is done through
something called "containerization".

What containerization does is create something that looks like a
private filesystem. If you make two containers, then you have two such
private filesystems. xraySpectacles and movingChargedParticles can now
run in their own containers, simultaneously, on the same server. When
they read and write files, they do so in their own private spaces. As
far as the running programs are concerned, they each have the computer
to themselves.

There are several different containerization approaches, of
course. The most common is Docker. There is also containerd which is
gaining popularity because it meshes well with some workload
management software called Kubernetes. In fact, Docker uses
containerd behind the scenes.

## Virtual Machines

Virtual Environments let us manage interwoven dependencies between
multiple Python packages and multiple versions of
libraries. Containerization let us isolate those programs even
further, giving each one of them their own filesystem. This is often
enough isolation, but not always. When multiple containers run on one
computer, they are still all executing on one running operating
system. What if there are programs that need specific versions of an
operating system? What if, indeed, the different programs need
entirely different operating systems? Virtualization is the answer.

With virtualization, the computer creates the illusion of being
several computers. This requires support at the deepest hardware level
of the CPU. Fortunately, essentially all modern CPUs can do this. With
the computer logically divided into many smaller ones, multiple
different operating systems can be loaded. For instance, one machine
can run ("host") five different versions of Linux, three versions of
Windows, and maybe even an instance of freeBSD. The computer hardware
handles all the details, doing things like manipulating the network
cards and disk controllers so they act like multiple ones.

One of the places where you're likely to see virtualization is on a
desktop ior laptop computer. In this case a program like VirtualBox
(for Windows) or UTM (for the Mac) is used to run a "guest" operating
system inside of the normal "host" operating system. This is how, for
instance, it's possible to run Windows on a Mac while it's running
other Mac programs. It's also how, behind the scenes, Microsoft's
Windows Subsystem for Linux (WSL2) runs Linux inside of a Windows
session.

Between Virtual Environments, Containers, and Virtual Machines there
is almost certainly some way to get the level of isolation and
encapsulation you need. Virtual Environments you can set up on your
own. Container setup requires additional permissions which will depend
to a degree on site-specific policy. Virtual Machines are a
heavyweight solution and usually require significant effort from the
system administration team. Knowing which one to use is mostly a
matter of deciding on what the minimum necessary level of isolation is
and then using the indicated strategy.
