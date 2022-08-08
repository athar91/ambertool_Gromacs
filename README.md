# ambertool_Gromacs
Always use pdb4amber to highlight the issue, if any or else make a amber compatible output file for antechamber 
pdb4amber -I *.pdb -o *pdb 
it will print protein vs non-protein with right atom types 

$AMBERHOME/exe/antechamber -i *.pdb -fi pdb -o *.mol2 -fo mol2 -c bcc -s 2 -nc 0 

 #alternatively once can use other charge scheme (than bcc)

$AMBERHOME/exe/parmchk -i sustiva.mol2 -f mol2 -o sustiva.frcmod 

 

For amber to gro file 

http://ambermd.org/tutorials/basic/tutorial4b/ 

$tleap -f oldff/leaprc.ff99SB 

>> source leaprc.gaff 
>> SUS = loadmol2 sustiva.mol2  
>> check SUS 
>> loadamberparams ligand.frcmod 
>> saveoff SUS sus.lib  
>> saveamberparm SUS sustiva.prmtop sustiva.rst7 ligand.inpcrd 
>> quit 

ALWAYS RUN TLEAP IN COMMAND, BECAUSE EVEN A SINGLE ERROR WILL STOP YOU FROM GETTING THE OUTPUT FILES 

And precisely check the forcefield, for lipid, use  

Remove all hydrogen while preparing from maestro and let tleap add 
