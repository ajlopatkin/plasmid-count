# plasmid-count
A small pipeline to count distinct plasmid replicons within assembled short/long-read sequences.

Parameters:

Input/Output
- `basedir`: top-level folder containing subfolders that contain assemblies.
- `file_dirs`: list of folders containing long and short read assembly `.fasta` files. These folders should be "flat", i.e., the should not contain subdirectories, and all `.fasta` files should be within these folders.
- `read_type`: a list of read types, either `long` or `short`, corresponding to the list of folders in `file_dirs`.
- `output_dir`: the target directory for output.

Filtering and Processing
`contig_len_cutoff`: minimum contig length to keep from PlasmidFinder output. Contigs below this threshold will not be processed.
`mash_cutoff`: mash distance cutoff to determine two contigs from the same sample identical; contigs below this cutoff will be merged.
`plasfinder_cov`: coverage theshold when running PlasmidFinder.
`plasfinder_pid`: percent identity threshold when running PlasmidFinder.
`read_threshold`: read count threshold for filtering assemblies; if read count is present in the contig header, and is less than this threshold, the contig will not be processed.
`cover_threshold`: coverage count threshold for filtering assemblies; if coverage is present in the contig header, and is less than this threshold, the contig will not be processed.
`blast_id_cutoff`: threshold for keeping BLAST results from a contig being compared to PLSdb.
`blast_len_thresh`: threshold for "long" vs. "short" contigs; controls overlap cutoff in stage 4.
`overlap_cutoff_short`: percentage of BLAST result overlap to trigger contig merging for "short" contigs.
`overlap_cutoff_long`: percentage of BLAST result overlap to trigger contig merging for "long" contigs.
`blast_len_cutoff`: threshold below which BLAST results will be discarded.
`filter_col`: filters all `Col`-like plasmids when set to `True`.
`filter_std`: filters high-variance contigs when set to `True`.

Usage:
1. Install the `plasmidcount` Conda environment using `conda create -f plasmidcount.yml`
2. Activate the environment using `conda activate plasmidcount`
3. Update the following parameters above
4. Navigate to the folder containing `plasmidcount.py` and run the script
