### USAGE

```sh
perl Illumina_Trim.pl $freads $rreads $minlen $maxlen $minQ $output_folder
  ```
  
where

- $freads = file path to forward reads
- $rreads = file path to reverse reads
- $minlen = discard all reads shorter than $minlen (default:50)
- $maxlen = trim reads to a maximum length of $maxlen (default:250)
- $minQ = trim all reads to a minimum Q score of $minQ (default:30)
- $output_folder = path to where output files should be written (default: current directory)

NOTE: Only $freads and $rreads are required.  If additional parameters are given, then all preceeding arguments are required. e.g. if $maxlen is defined then you also have to include $minlen, but not $minQ or $output_folder.

### WHAT DOES IT DO ?

```sh
GENERATE QC REPORT BEFORE TRIMMING

       ;;;;;
       ;;;;;
       ;;;;;            (FastQC)
     ..;;;;;..
      ':::::'
        ':`

REMOVE NEXTERA ADAPTERS IF PRESENT

       ;;;;;
       ;;;;;
       ;;;;;            (TrimGalore)
     ..;;;;;..
      ':::::'
        ':`

FIND CONTAMINAITNG ILLUMINA ADAPTERS OR OTHER OVERREPRESENTED SEQUENCES


       ;;;;;
       ;;;;;
       ;;;;;            (Custom perl code)
     ..;;;;;..
      ':::::'
        ':`

REMOVE ILLUMINA ADAPTERS AND OVERREPRESENTED SDEQUENCES

       ;;;;;
       ;;;;;
       ;;;;;            (Cutadapt)
     ..;;;;;..
      ':::::'
        ':`

TRIM TO Q30

       ;;;;;
       ;;;;;
       ;;;;;            (HomerTools)
     ..;;;;;..
      ':::::'
        ':`

REMOVE POLY A ARTIFACTS


       ;;;;;
       ;;;;;
       ;;;;;            (HomerTools)
     ..;;;;;..
      ':::::'
        ':`

TRIM SEQUENCES TO $minlen $maxlen $minQ; REMOVE UNPAIRED REDAS

       ;;;;;
       ;;;;;
       ;;;;;            (Trimmomatic)
     ..;;;;;..
      ':::::'
        ':`

WRITE FASTQ AND FASTA FILE

       ;;;;;
       ;;;;;
       ;;;;;            (Biopieces)
     ..;;;;;..
      ':::::'
        ':`

GENERATE QC REPORT AFTER TRIMMING

       ;;;;;
       ;;;;;
       ;;;;;            (FastQC)
     ..;;;;;..
      ':::::'
        ':`

FINAL QCed OUTPUT FILES

```
  
