# tgrep2

The primary function of TGrep is to extract parse trees whose structures match a specified pattern. It is, essentially, grep for trees.

## Basics

General usage:

`tgrep2 [options] <pattern>...`

Search for all instances of the word "some." 

`tgrep2 "some"`

Return all full sentences with the word "some."

`tgrep2 -w "some"`

Return only the terminal nodes (i.e., the words), without parses.

`tgrep2 -wt "some"`

Pipe the output into `less` so we can scroll up and down.

`tgrep2 -wt "some" | less`

How many matches are there?

`tgrep2 -wt "some" | wc -l`

Make sure to get all subtrees matching one or more patterns, but only report each subtree once (use `-af` by default, it will make the results more accurate).

`tgrep2 -afwt "some" | wc -l`

Once we're happy with our results, we can save them to a file.

`tgrep2 -afwt "some" > "some.txt"`

By default, `tgrep2` searches the Switchboard (or whatever the `TGREP2_CORPUS` environment variable is set to). Let's search a different corpus instead. To see the available corpora:

`ls $TGREP2ABLE`

Let's search the BNC.

`tgrep2 -afwtc /afs/ir/data/linguistic-data/Treebank/tgrep2able/bnc-charniak-parses.t2c.gz "some" | wc -l`


## Tree search

Let's go back to the Switchboard and find all the "some"-NPs. Start by looking at the parses with the `-l` option.

`tgrep2 -aflw "some" | less`


Find the NP that dominates "some."

`tgrep2 -aflw "some >> NP" | less`


Oops, this still gets us just the word "some." TGrep2 returns the first node by default. Let's turn the pattern around.

`tgrep2 -afl "NP << some" | less`

The problem is that this finds any NP with "some" in it. Let's get the closest one.

`tgrep2 -afl "NP @<< NP << some" | less`

Let's find the cases of partitive "some." 

`tgrep2 -afl "NP << some << (of , some)" | less`

Let's find the cases of non-partitive "some."

`tgrep2 -afl "NP << (some @. of)" | less`

Let's find the cases of "some"-NPs at the start of sentences.

`tgrep2 -afl "NP << some @, *" | less`

Let's specify that the NP must contain a head noun.

`tgrep2 -afl "NP=np << (some .. (/NN|NNS/ >> =np))" | less`


## Moving away from simple pattern searches and towards building databases automatically: TDTlite
