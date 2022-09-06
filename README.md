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

2. The json files include new data and information about assemblies:
- List of valid interfaces of protein complexes (polymer-polymer interactions) 
- List of Vander Waals contacts (cutoff 5 Angstroms)
- Interface uniprot accesion and sequence position of the UniProt entry that corresponds to the residue mapping 
- Author atom sequence identifiers for contacts at the interface
- Asym chain identifiers in the original model file for interface atoms
- sequence number for interface atoms (label)
