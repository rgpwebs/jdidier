---
title: "Protein-ligand Dockings. Concepts and applications"
description: "Here we learn about the ground of Protein-Ligand Dockings"
menu:
  teaching:
    parent: Subjects
---

# Day 1

## Hands-on 1 - Introduction to UCSF Chimera.

[Download Slides here](https://drive.google.com/file/d/1c5HLCtYUCxjTUsMZdZ63Hzud_8vxxnqQ/view?usp=sharing)

***Any*** modelling of biochemical processes starts with a good understanding of the **structural properties** of the molecules under study. Available pdb structures of the protein, their atomic resolution, their state of complexation are, in between others, the key variables to analyse prior to modelling. Before getting into the core of the protein-ligand docking exercise, we first need to get used to the exloration of biomolecular constructs with efficient visualizing, analysis and building tools.

For this course, our bet is to work with [UCSF Chimera](https://www.cgl.ucsf.edu/Chimera/); a freeware for academic purposes. Details on the story of Chimera will be given during the lessons.

Our first case study system for this course are **hormone receptors**. Look at the available structures of human androgen receptor binding protein at the [Protein Data Bank](http://www.rcsb.org/). Once overviewed all the available information, we will focus on HAR complexed with testosterone (PDB ID: `2am9`).

A lot of information are provided in the same `2am9.pdb` file. However, most of information is reachable directly from the webpage interface or from visualizing programs (i.e. Chimera).

Try to answer:

- What is the resolution of the structures?

- What is the experimental method used to characterize it?

- How many chemicals are present in the resolved structure?

- How long is its sequence?

After answering those questions, let's look at the structure and explore it.

### Menus and Functions in UCSF Chimera ###

UCSF Chimera affords with three levels of interactions for users:

1. Menus - Like in  any modern interface, users can work with Chimera using menus, clicks and pop-ups.
2. Command lines - Chimera has its own language for defined actions and this allows us to go a lot faster than menu practise. The teacher will explain you how to activate it and use it.
3. Python coding - Pretty much eveything in Chimera is embedded in python - a very powerful and agreable programming language. Almost eveything can be piloted from the python interpreter.

Most of what we will do in this course will mix the first and the second approach.

During the flow of the course, we will learn Chimera's functions that will be particularly important for everything we need. All command lines and menu functions could be found in the Chimera's website. But we will construct together the following table:

Action | Reference Menu | Command line | Mouse tool
-------|----------------|--------------|-----------
Open a file | File> Open | `open` |
Select Atom | Action> Select | `sel @` | CTRL+left click
Select Residue| Action> Select | `sel :` | CTRL+left click
Select molecules | Action> Select| `sel #`|
Select by keyword | Action> Select| `sel keyword`|
Change Color | Action> Color | `color` |
Change the atomic representation of molecules, residues, atoms, ligands | | `rib`, `repr` |

Know the syntaxis for the selection, modification and other actions on atoms.

Other functions we'll study could be of interest. Do not doubt in asking for them.


### Binding site exploration ###

As mentioned in the course, when information about the chemical binding sites are blur or absent, one way to move forward is to do a cavity search or blind docking experiments. In this part of the course, we will go for the former.

Remove all the ligands from the 2am9 pdb opened in Chimera. Then follow this sequence:

```
Menu Tools --> Surface/Binding Analysis --> Surfnet
```

Then in the section *Atom Set 1:* just enter `:*` (meaning that Surfnet will consider all atoms of the systems to look for cavities).

In the Cavity radius enter `1.0` (aprox. the diameter of a water molecule). Many sites appears. Look at the biggest. Then try to reduce the noise, but increase the radius of the search (i.e. `3.0`).

What can you concluded regarding the possible binding sites?

### Studying the experimental complexes

Close all the models you loaded in UCSF Chimera (command line: `close all`). And open back the `2am9` structure (command line: `open 2am9`). Look at all the none proteic structures (command line: `sel ligand`). Could you recognize those species mentioned in the PDB Web page? Could you differentiate crystallographic agents from the natural ligand of the protein?

One of the driving forces in molecular recognitions are mainly polar and hydrophobic. Look at the binding site of the testosterone i.e. looking at everything that stands at 2-3 Angstroms for it (command line: `show :TES zr < 3`). Look at all the residues involved. Could you answer those questions: Is the binding site mainly polar or hydrophobic? Are some residues key for the orientation of the testosterone?


### Generating graphical material

A major part of what modelers present has a tremendous graphical relevance. Pictures, graphs and movie are fundamental to crystallize a given concept or result. In this hand on, we will learn to use Chimera to present molecular information (that will be posteriorly used for representing docking results).

Provide some clear pictural representations of:

1. the protein on its whole
2. the binding site
3. the interactions of the binding site and any idea you have to get a 2-dimensional impression of the 3-dimensional reality.


### Additional works

Once you have get used to with this initial structure, compare it with other crystalographic structures related to it (look at the PDB webpage to do so). From the different interesting things we could do here, we can look at the structure obtained with different androgen like compounds (e.g. testosterone in PDB `2ama`) compare the binding poses of the ligand for the different structure, also compared to some prostate treatment compound, with the structure some mutants of the protein that are resistant to prostate treatment, and finally with a progesterone binding protein. Discuss on the nature of the structures, the type of interactions between the ligand and the protein, etc.

In this case aligning the proteins will be a particularly useful tools to do so. The matchmaker tool (in `Tools --> Structure Comparison --> MatchMaker`) is a possible option. The related command line is `mm #num_reference_model #num_target_model`)

