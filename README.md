# PISA interaction interface and assembly JSON specifications

PISA (Protein Interfaces, surfaces and assemblies) is a software that can analyse macromolecular interaction interfaces of proteins and nucleic acids and identify probable quaternary structures and assemblies.

PISA perfoms the following tasks:

1. Analyse macromolecular interaction interfaces 
2. Identify probable assemblies
3. Perform database searches to find structurally similar interfaces and assemblies

The PDBe implementation of PISA is based on CCP4 PISA. For more information about PISA software, see the [CCP4 PISA documentation page](https://www.ccp4.ac.uk/html/pisa.html).

## PISA API endpoints migration

**On TBD [every PISA API endpoint](https://www.ebi.ac.uk/pdbe/api/doc/pisa.html) will be retired and replaced with two new API endpoints (see details below).**

If you wish to receive updates about these changes, consider subscribing to the following mailing lists:

*pdbe-api-users@ebi.ac.uk*

*pdbe-api-developers@ebi.ac.uk* 

## Legacy API

The old API points that will be retired on the 17th October 2022 can be found at https://www.ebi.ac.uk/pdbe/api/doc/pisa.html

## New API endpoints

### API specification
There are two new API endpoints which return responses in JSON format. The data are obtained from PISA and contain information about protein interfaces and assemblies. The JSON schemas of these two endpoints are [available at Apiary](https://pisalite.docs.apiary.io/#reference/0/pisaqualifierjson/interaction-interface-data-per-pdb-assembly-entry).

### Data description
The JSON response `{pdb_id}-assembly{assembly_id}interfaces.json` includes new data and information for interfaces and assemblies:
- New assembly information: 
  - Size of the assembly
  - Dissociation energy
  - Accessible surface area
  - Entropy
  - Dissociation area
  - Solvation energy gain
  - Formula
  - Composition.
- Removed interface information: 
  - CSS
  - Overlap
  - X_rel
  - Fixed 
  - Interface type 
  - Number of occurances
- List of valid interfaces of protein complexes (polymer-polymer interactions) 
- List of van der Waals contacts (with a cutoff of 5 Angstroms, labelled as 'other bonds')

Information added for every contact (for `atom1` and `atom2`):

- Residue names (Three-letter code)
- Author chain identifier
- Interface UniProt accesion numbers
- Sequence position of the UniProt entry that corresponds to the residue mapping 
- Author atom sequence identifiers 
- Asym chain identifiers in the original model 
- Sequence number (label)
- Atom insertion code

The JSON data from `{pdb_id}-assembly{assembly_code}.json` replaces the legacy PISA API endpoint https://www.ebi.ac.uk/pdbe/api/pisa/asis/:pdbid/:assemblyidwill. No new data has been added, and the data structure is identical between the old and the new versions. The only difference is that the new version of the data is obtained from the new PDBe PISA implementation.

## Examples 

The following examples show the new data of the PISA API endpoints, for various macromolecular complexes. Examples include protein assemblies with different number of components (monomer, dimer, tetramer, nonamer), a viral assembly, and a protein-DNA complex (Transposase complexed with tramposon end DNA).

The [examples](https://github.com/PDBe-KB/pdbe-pisa-json/tree/main/examples) folder in this repository contains the following:

- [1j6z](https://github.com/PDBe-KB/pdbe-pisa-json/tree/main/examples/monomer_1j6z): Monomer; [Actin](https://www.ebi.ac.uk/pdbe/entry/pdb/1j6z)
- [6nrx](https://github.com/PDBe-KB/pdbe-pisa-json/tree/main/examples/dimer_6nrx): Dimer; [DIP-eta IG1 homodimer](https://www.ebi.ac.uk/pdbe/entry/pdb/6nrx)
- [1fqy](https://github.com/PDBe-KB/pdbe-pisa-json/tree/main/examples/tetramer_1fpy): Tetramer; [Aquaporin](https://www.ebi.ac.uk/pdbe/entry/pdb/1fqy)
- [2cha](https://github.com/PDBe-KB/pdbe-pisa-json/tree/main/examples/nonamer_2cha): Nonamer; [Crymotripsin](https://www.ebi.ac.uk/pdbe/entry/pdb/2cha)
- [1ruz](https://github.com/PDBe-KB/pdbe-pisa-json/tree/main/examples/virus_1ruz): Viral assembly; [Influenza virus](https://www.ebi.ac.uk/pdbe/entry/pdb/1ruz)
- [1muh](https://github.com/PDBe-KB/pdbe-pisa-json/tree/main/examples/complex_dna_1muh): protein/DNA complex; [Transposase complexed with DNA](https://www.ebi.ac.uk/pdbe/entry/pdb/1muh)

### Simple example of assembly interfaces JSON
```
{
    "PISA": {
        "pdb_id": "1j6z", 
        "assembly_id": "1", 
        "pisa_version": "2.0", 
        "assembly": {
            "mmsize": "1", 
            "dissociation_energy": -3.0, 
            "accessible_surface_area": 16576.74, 
            "buried_surface_area": 2013.44, 
            "entropy": 4.85, 
            "dissociation_area": 322.74, 
            "solvation_energy_gain": -57.49, 
            "formula": "Aa(6)bc", 
            "composition": "A[CA](6)[ADP][RHO]", 
            "interface_count": 0, 
            "interfaces": []
        }
    }
}
```

### Simple example of assembly JSON
```
{
    "PISA": {
        "pdb_id": "1j6z", 
        "assembly_id": "1", 
        "pisa_version": "2.0", 
        "assembly": {
            "id": "1", 
            "size": "9", 
            "score": "", 
            "macromolecular_size": "1", 
            "dissociation_energy": -3.0, 
            "accessible_surface_area": 16576.74, 
            "buried_surface_area": 2013.44, 
            "entropy": 4.85, 
            "dissociation_area": 322.74, 
            "solvation_energy_gain": -57.49, 
            "number_of_uc": "0", 
            "number_of_dissociated_elements": "2", 
            "symmetry_number": "1", 
            "formula": "Aa(6)bc", 
            "composition": "A[CA](6)[ADP][RHO]", 
            "R350": ""
        }
    }
}
```

## Versioning

We use [SemVer](https://semver.org) for versioning.

## License

All the data are made available under [CC-BY 4.0 license](https://creativecommons.org/licenses/by/4.0/). All the source code is available under [Apache 2.0 license](https://github.com/PDBe-KB/pdbe-pisa-json/blob/main/LICENSE).

## Authors
* [Grisell Diaz Leines](https://github.com/grisell) - Lead developer
* [Mihaly Varadi](https://github.com/mvaradi) - Review and management 

To contribute, please refer to the [contribution guidelines](https://github.com/PDBe-KB/pdbe-pisa-json/blob/main/CONTRIBUTING.md).
