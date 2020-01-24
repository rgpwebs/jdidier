---
title: "Module4_Python_UCSFChimera"
description: "BLa bla bla "
menu:
  teaching:
    parent: "MSc Bioinformatics"
--- 

> These are some of the functions that we have been working on during the practicum we did on UCSF Chimera and python for molecular handling. 

<p>Remember that the best way to move forward in this field consists in having the commandline activated in a window of the program and to aactivate the Python IDLE (that you can find by going to Favorites)</p>

> To call command line functions directly from the idle.

from chimera import runCommand as rc

> open a file in UCSF Chimera thoughout the python interpreter.
rc("open 1r4c")


> To define list of atoms that could be used for further works
> This syntax is valid given that you have molecules or part of them selected in the main window

sel=chimera.selection.currentAtoms()
sel_res=chimera.selection.currentResidues()

> Looping in list? Something like:

for atoms in sel:
	print atoms

> You just generated the array containing all the atoms and the residues respectively in sel and sel_res.
> so you can access to a given element of the array

print sel[0]

> But obviously the interesting part goes when we can make somekind of application like:

for atoms in sel:
	print sel[0].xformCoord().distance(atoms.xformCoord())

> There is a long list of attributes that are accessible

> We can also use those attributes 

for atoms in sel:
	if atoms.residue.isHelix == True:
		print atoms


