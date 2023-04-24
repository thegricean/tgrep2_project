---
layout: page
title: Setup
nav_order: 1
description: >-
    Setting up tgrep2 and TDTlite.
---

# Setup
{:.no_toc}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

These setup instructions are specific to Stanford affiliates. You will access both TGrep2 and TDTlite via AFS. For information on how to set up the TGrep2/[TDT](https://github.com/thegricean/TDTlite) pipeline at a different institution, feel free to email Judith Degen at jdegen@stanford.edu. (Documentation forthcoming.)

## Preliminary steps

TGrep2 and TDTlite require perl and Python. 

To use TGrep2, you’ll need to log onto a server with an AFS mount. Cardinal works as of April 2023. 

Before you can access the tools, you must ask the corpus TA to add your SUNet ID to the `corpora-general` group. Go [here](https://linguistics.stanford.edu/resources/resources-corpora/corpus-ta) to see who is the current corpus TA. Once you have been added to the group, following the remaining instructions.


## TGrep2 and TDTlite setup

Log onto a server. In your terminal, type:

```ssh SUNET@cardinal.stanford.edu```

Enter your password at the prompt and complete 2-factor authentication. You will be transported to your home directory.

Add the following to your bash profile:

```
export PATH=$PATH:~/.gem/bin:/afs/ir/data/linguistic-data/bin/linux_2_4:/afs/ir/data/linguistic-data/TDTlite:~/bin

export TGREP2ABLE=/afs/ir/data/linguistic-data/Treebank/tgrep2able/

export TDTlite=/afs/ir/data/linguistic-data/TDTlite/

export TGREP2_CORPUS=$TGREP2ABLE/swbd.t2c.gz

export TDT_DATABASES=/afs/ir/data/linguistic-data/TDTlite/databases/
```


If you're not sure how to access your bash profile:

1. At the prompt, type:

```vi .bash_profile```

2. To get into insert mode, type the letter `i`. Copy and paste the above content into the very start of the file. Make sure to press Enter after you have pasted to make sure there is a line separating the pasted content from any following content.

5. Save and exit as follows:
Press the Esc key. Enter a colon, then the letters `wq` and press Enter.

Source the bash profile:

```source .bash_profile```

Now you should be able to access TGrep2 and the TDT. Typing `tgrep2` at the prompt should print usage information for TGrep2. Typing `run -h` at the prompt should print usage information for TDTlite. You're all set! Check out the [tutorials](https://thegricean.github.io/tgrep2_tdtlite/tutorials/) for how to get started.


## Checklist

Here is a recap of all the things that should be set up on the server.

* Your SUNet has been added to `corpora-general` by the corpus TA.
* You have set the relevant environment variables in your bash profile.