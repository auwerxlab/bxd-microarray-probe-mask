# BXD microarray probe mask

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.4722913.svg)](https://doi.org/10.5281/zenodo.4722913)

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International License</a>.

© Copyright 2021 Laboratory of Integrative Systems Physiology, EPFL, Switzerland

This project is based on the following template: https://github.com/auwerxlab/renku-project-template/tree/master/R-renv (deb856b)

This is a Renku project, see https://renku.readthedocs.io for details.

**Authors:** Alexis Rapin (alexis.rapin@epfl.ch), Alexis Bachmann (alexis.bachmann@epfl.ch), Maroun Bou Sleiman (maroun.bousleiman@epfl.ch)

## Description

This R project generates lists of probes targeting polymorphic regions in the BXD mouse population for diverse microarray platforms (a.k.a. "probes kill lists" or "masks").


Comparing a transcript expression levels between strains using microarrays can be biased if the transcript carries a genetic variation across strains, as different variants would have different hybridization affinity for the probe. To remove this bias, it is important to identify which probes target transcripts showing variations across the strains. These probes could then be ignored when computing expression levels.


The [BXD mouse genetic diversity panel](https://doi.org/10.1016/j.cels.2020.12.002) results from an original cross between a female C57BL/6 and a male DBA/2J. It is therefore sufficient to identify probes targeting a region in which a variant between C57BL/6 and DBA/2J exists.

## Ressources

- Project repository: https://sv-renku-git.epfl.ch/lisp/bxd-microarray-probe-mask
- Github archive repository: https://github.com/auwerxlab/bxd-microarray-probe-mask
- Zenodo archive repository: https://doi.org/10.5281/zenodo.4722913
- DBA/6J SNPs: ftp://ftp-mouse.sanger.ac.uk/current_indels/strain_specific_vcfs/DBA_2J.mgp.v5.snps.dbSNP142.vcf.gz
- DBA/6J indels: ftp://ftp-mouse.sanger.ac.uk/current_indels/strain_specific_vcfs/DBA_2J.mgp.v5.indels.dbSNP142.normed.vcf.gz
- Affymetrix Clariom S Assay, Mouse support files: https://media.affymetrix.com/analysis/downloads/lf/xta/Clariom_S_Mouse

## Get this project

You can clone this project from https://sv-renku-git.epfl.ch:
```
$ git clone https://sv-renku-git.epfl.ch/lisp/bxd-microarray-probe-mask.git
```

If it is private, you would need a valid Gitlab token. Contact the authors if needed, or consider using a public archive (see below).
```
$ git clone https://< gitlab_token_name >:< gitlab_token >@sv-renku-git.epfl.ch/lisp/bxd-microarray-probe-mask.git
```

### Get a project archive

This project is publicly released as an archive which contains all the essential files (see the Data section below).


You can clone the archive from https://github.com:
```
$ git clone https://github.com/auwerxlab/bxd-microarray-probe-mask.git
```

And download it from https://zenodo.org at https://doi.org/10.5281/zenodo.4722913.

## Requirements

- R version 4.0.0
- renv R package
- See renv.lock for the complete list of R packages dependencies
- See Dockerfile for more system requirements

## Data

Only essential data are archived. These include:

- **Microarray probes "kill lists":** "killing lists" identifying probes targeting polymorphic regions in the BXD strains are included in ``data/platform_files/< platform_id >/kill_list/kill_list_< platform_id >.txt``.

Data that are not archived include:

- **Microarray platform support files:** Support files are not included. See ``data/microarray_runs.txt`` for sources.

## Usage

Run the ``notebook/setup.Rmd`` notebook first, then other notebooks located in ``notebooks/``:

- ``notebook/setup.Rmd``: General setup.
- ``GPL23038_Affymetrix_Clariom_S_Assay_Mouse.Rmd``: Create kill list for [Affymetrix Clariom S Assay, Mouse](https://www.thermofisher.com/order/catalog/product/902930) (Thermofisher, cat.no. 902930, GEO accession [GPL23038](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GPL23038)).

Render notebooks and archive essential files using ``make``:

```
$ make
render               render all R notebooks located in notebooks/
commit               run git commit
archive              create an archive of this project in archive/ (CAUTION: will not include LFS objects)
```

## Structure

<pre>
.
├── archive                   Archives of this repos (not available in an archive itself)
├── data                      
│   └── < platform_id >       
│       └── kill_list         Probes "kill lists" for each platform
├── notebooks                 R notebooks
└── renv                      renv directory (set as a symbolic link in renku projects, not available in an archive)
</pre>

