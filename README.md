## PISA-lite
PISA-lite (Protein Interfaces, surfaces and assemblies) is a softaware developed for the investigation of macromolecular interfaces (such as proteins, DNA/RNA and ligands) and for the identification of probable quaternary structures or assemblies. 

PISA can perfom the following tasks :

1. Explore and identify macromolecular interfaces 
2. Identification of probable assemblies
3. Database searches of structurally similar interfaces and assemblies

The code is the latest version of the PISA code used in CCP4. For more information about PISA software :
https://www.ccp4.ac.uk/html/pisa.html

## News: PISA API endpoints migration

On 17th October all PISA API endpoints(https://www.ebi.ac.uk/pdbe/api/doc/pisa.html ) will be retired and replaced with two new API endpoints (see description below).

If you wish to receive updates about these changes, subscribe to the mail lists :

*pdbe-api-users@ebi.ac.uk*

*pdbe-api-developers@ebi.ac.uk* 

## Legacy API

The old API points that will be retired on 17th October can be found here:

https://www.ebi.ac.uk/pdbe/api/doc/pisa.html

## New API endpoints

1. There are two new API enpoints that consists of two json files. These files are obtained with PISA and contain information about protein interfaces and assemblies. The json schemas of these two files can be found here: 

https://pisalite.docs.apiary.io/#reference/0/pisaqualifierjson/interaction-interface-data-per-pdb-assembly-entry

2. The json file {pdb_id}-assembly{assembly_id}interfaces.json includes new data and information for interfaces and assemblies:
- Assembly information has been added: Size of the assembly, dissociation energy, accessible surface area, entropy, dissociation area, solvation energy  gain, formula and composition.
- Interface information removed: css, overlap, x_rel, fixed, interface type, number of occurances
- List of valid interfaces of protein complexes (polymer-polymer interactions) 
- List of van der Waals contacts (cutoff 5 Angstroms, labelled as 'other bonds')

Information added for every contact (for atom1 and atom2):

- Residue names (Three-letter code)
- Author chain identifier
- Interface uniprot accesion numbers
- sequence position of the UniProt entry that corresponds to the residue mapping 
- Author atom sequence identifiers 
- Asym chain identifiers in the original model 
- sequence number (label)
- Atom insertion code

3. {pdb_id}-assembly{assembly_code}.json is data used in one PISA API in the entry pages: https://www.ebi.ac.uk/pdbe/api/pisa/asis/:pdbid/:assemblyidwill. There is not new data added in this PISA API.  The only change is an update in the PISA version to obtain this data.

## Examples 

