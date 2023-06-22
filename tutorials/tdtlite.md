---
layout: default
title: TDTlite Tutorial
parent: Tutorials
nav_order: 2
---


# TDTlite
{:.no_toc}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

In this tutorial, you'll set up a simple TDTlite project culminating in a .tsv database of instances of "some" with additional information about each instance -- e.g., the match's unique TGrep2 ID, the full sentence, whether "some" occurs in the partitive, and whether "some" occurs at the start of a sentence. To do this easily, use TDTlite, a wrapper that allows for batch calling of perl scripts that make up the TDT.

Throughout this tutorial, we will be using examples from the alt-right news site "Breitbart", investigating how they use language to talk about transgender and non-binary individuals. 

## Set up the project structure

This section provides a project structure skeleton for setting up your project. We'll go into more detail about what each of these folders and files does in time, but to begin you should have a "project" folder. This will house all the files needed for your project. Inside of this folder, you should have:

1) A "ptn" folder. This folder consists of two subfolders, called "StringVar" and "CatVar".

2) A "data" folder. 

3) A "results" folder. This is where the results of your queries will go.  

You can find the structure you will need represented visually below:

![A project structure tree](https://github.com/thegricean/tgrep2_tdtlite/blob/main/assets/images/tdtLiteStructure.png?raw=true)

## Add a MACROS file

Next, you'll want to create a MACROS.ptn file inside the project folder. This folder will store all the tgrep patterns that you will be able to call in your other pattern files.

A good couple of default patterns include:

```
@ WORD  /^'{0,1}[a-zA-Z]+.*/;
@ TERMINAL  * !< *;
@ NP    /^NP/;
@ VP    /^VP/;
@ PP    /^PP/;
@ DISFL /EDITED|UH|PRN|-UNK/; 
```

Note the structure of each macro: on a new line, place an "@", followed by a single space and the name of the macro in all caps. Then tab once and write out the macro, and end each macro with a semicolon.

You will also want to add the specific patterns that you're going to make regular use of in your investigation. For example, we might want to be able to find the sentences that contain the bigrams "trans(gender) woman" and "biological male". We can turn these into macros that we can use later:

```
@ BIOMAN  /biological/ . /\bmale\b|\males\b/;
@ TRANSWOMAN    /trans|transgender/ . /woman|women/;
```

Note that the '\b' delimiter is used here to ensure we don't erroneously pick out 'biological female'.



## Create pattern files

## Search the corpus and build your database

