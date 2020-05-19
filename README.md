# IReDATA
As part of the [CHEMeDATA initiative](https://github.com/CHEMeDATA), here is the starting point of a proposition of standard to report the assignment of IR spectra.
## General idea
By analogy to NMReDATA, we shall use a .sdf (data structure format) file. The SDF file includes a structure in the .mol format. In the [the most common](https://chem.libretexts.org/Courses/University_of_Arkansas_Little_Rock/ChemInformatics_(2017)%3A_Chem_4399%2F%2F5399/2.2%3A_Chemical_Representations_on_Computer%3A_Part_II/2.2.2%3A_Anatomy_of_a_MOL_file) variant the atoms are listed with their coordinates. Follows the list of bonds.
## Reference to the atoms
For stretch (involving pairs of atoms), the reference to bond number (in the list of bonds) is the most obvious. But this is not easily extendable to bend and out-of-plane vibrations. Refering to atom index is more generalizable. Because of degeneracy (symmetry of two OH of water), presence of multiple non-distinguished vibrations (alkyl chain), an observed vibration can be attributed to multiple bonds, each in separate [] (*see example*). 
## Reference to the atoms

|code|type of vibration|prefix subtype|comments|
|----|-----------------|-------|-------|
|st.|stretching|sym: symmetric asym: asymetric|(br.) for broad signals (str.) for strong|
|bend.|bending|sym: symmetric asym: asymetric||
|oop.|out-of-plane vibration|||

For water...
```
H2O
APtclcactv05172014203D 0   0.00000     0.00000
 
  3  2  0  0  0  0  0  0  0  0999 V2000
   -0.0000   -0.0589   -0.0000 O   0  0  0  0  0  0  0  0  0  0  0  0
   -0.8110    0.4677    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
    0.8110    0.4677    0.0000 H   0  0  0  0  0  0  0  0  0  0  0  0
  1  2  1  0  0  0  0
  1  3  1  0  0  0  0
M  END
```
... a pre-proposition of sdf tag for the assigment of wibration of water would be:
```
>  <IReDATA>
3657, (br) sym st., [1, 2], [2, 3]
3755, asym st., [1, 2], [2, 3]
1595, bend., [1, 2, 3] ; fist atom in the list is the pivot

```
We should probably only list atoms from the [local-mode](http://www.fclab2.net/definitions.html) vibrations.
## Molecular vibrations
Shall the format be able to fully describe complex vibrations, or only functional groups?
For molecular vibration should we list atoms in (2 or more?) blocks moving one relative to the other?
Among others, Gaussian can provide vibration [information](http://gaussian.com/freq/) on optimized geometries.

## Relevant work
JSmol [visualisation of the vibrations](https://chemapps.stolaf.edu/jmol/jsmol/jsv_mol.htm) obtained by manual assignment of an IR spectrum. The [jcamp](data/acetophenone.jdx) file with embeded mols and vibration data and more info [here](https://chemapps.stolaf.edu/jmol/docs/misc/Jmol-JSpecView-specs.pdf).


## Please contribute!
Just [leave a comment](https://github.com/CHEMeDATA/IReDATA/issues/new/choose).


