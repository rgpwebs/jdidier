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


# Days 2 and 3

[Download Slides here](https://drive.google.com/file/d/1XWlGbeFHx9vETIOBUflXYvhYGIztotek/view)

Autodock is a flexible ligand-protein docking program which basically runs as a two steps procedure: the calculation of the map of interactions of the binding site with some general atom types (performed with autogrid) and the posing of the lligand respecting this map of interaction (performed with autodock).

Some of the  algorithms detailed during the  theoretical courses are available in Autodock. The actual version of the program  (the version we will use here) is the version 4.0 which provides with important new features for docking prospect like protein residue flexibility and high quality scoring functions.

In this tutorial, you will be introduced the docking approaches by  undertaking undertaking on your own some docking experiments on the androgen binding receptor seen in the tutorial I. The different steps for the initial study as well as the possible extension of the work are summarize below.

In the recent years, Autodock has been updated by an external group to give raise to Autodock vina. This version has a slightly accelerated version of the code and is easier to perform. UCSF Chimera has followed the lead and now has an integrated interface into the same program.

Autodock scoring function is applied using an adapted AMBER force field therefore the atoms of the protein and the ligand have to be set up in accordance with  this ff. Autodock computes the possible interaction points in the binding site of the protein prior to exploring the conformations. Our next step is therefore to set up the grid.

**1 - Ligand and Protein Set up**

In Chimera, we need to prepare first the two structures indepently, the ligand and the receptor. To do so, following with what you learned during the previous day:

- open the `2am9` structure
- remove all ligands and water molecules (solvent)
- once cleaned use the dock prep interface (Tools --> Surface/Binding Analysis --> DockPrep) to add hydrogen and clean any other possible problems (i.e. rotameric states, etc...)
- then same the mol2 of the resulting receptor (i.e. with name `receptor.mol2`)

Proceed the same way with the ligand (this time start by removing all the atoms of the protein and only keep the testosterone)

**2 - Run the calculation**

Once both mol2 files have been generated, open them back in Chimera and then go to the same menu than before selection this time the **Autodock Vina** entry.

A new window pops up. There, select the name of the output file in the ligand and receptor section. Double check that you correctly selected the right models for both receptors and ligand! Finally, you have to define the region of the space where the calculation will be performed. To do so, use the 3D handling of the mouse (middle button) for the protein region.


1. Analysis
Once the calculation ends, a window will appear with the results of the docking. Open back the original structure and compare the predicted versus the original structures.


4. Look in the pdb at the structure of some mutant resistant in prostate cancer treatment. Look at the binding site form of the structure. What could you conclude? What about docking in this structure?


### Additional works

Once you have get used to with this initial structure, compare it with other crystalographic structures related to it (look at the PDB webpage to do so). From the different interesting things we could do here, we can look at the structure obtained with different androgen like compounds (e.g. testosterone in PDB `2ama`) compare the binding poses of the ligand for the different structure, also compared to some prostate treatment compound, with the structure some mutants of the protein that are resistant to prostate treatment, and finally with a progesterone binding protein. Discuss on the nature of the structures, the type of interactions between the ligand and the protein, etc.

In this case aligning the proteins will be a particularly useful tools to do so. The matchmaker tool (in `Tools --> Structure Comparison --> MatchMaker`) is a possible option. The related command line is `mm #num_reference_model #num_target_model`)

