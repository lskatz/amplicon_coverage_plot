# amplicon_coverage_plot
[![DOI](https://zenodo.org/badge/270555241.svg)](https://zenodo.org/badge/latestdoi/270555241)
[![Build Status](https://travis-ci.org/chienchi/amplicon_coverage_plot.svg?branch=master)](https://travis-ci.org/chienchi/amplicon_coverage_plot)
[![codecov](https://codecov.io/gh/chienchi/amplicon_coverage_plot/branch/master/graph/badge.svg)](https://codecov.io/gh/chienchi/amplicon_coverage_plot)

The script will generate an [interactive barplot](https://chienchi.github.io/amplicon_coverage_plot/index.html) given amplicon info in bed/bedpe format and coverage information in cov/bam file.

## Dependencies

### Programming/Scripting languages
- [Python >=v3.7](https://www.python.org/)
    - The pipeline has been tested in v3.7.6

### Python packages
- [numpy >=1.15.1](http://www.numpy.org/) 
- [plotly >=4.7.1](https://plotly.com/python/)
- [pysam >= 0.15.4](https://github.com/pysam-developers/pysam)

### Third party softwares/packages
- [samtools >=1.9](http://www.htslib.org) - process bam file

## Installation

### Install by pip

```
pip install amplicov
```

### Install from source
Clone the `amplicon_coverage_plot` repository.

```
git clone https://github.com/chienchi/amplicon_coverage_plot
```

Then change directory to `amplicon_coverage_plot` and install.

```
cd amplicon_coverage_plot
python setup.py install
```

If the installation was succesful, you should be able to type `amplicon_coverage.py -h` and get a help message on how to use the tool.

```
amplicov -h
```


## Usage
```
usage: amplicov [-h] (--bed [FILE] | --bedpe [FILE])
                (--bam [FILE] | --cov [FILE]) [-o [PATH]] [-p [STR]] [--pp]
                [--version]

Script to parse amplicon region coverage and generate barplot in html

optional arguments:
  -h, --help            show this help message and exit
  --pp                  process proper paired only reads from bam file
                        (illumina)
  --version             show program's version number and exit

Amplicon Input (required, mutually exclusive):
  --bed [FILE]          amplicon bed file
  --bedpe [FILE]        amplicon bedpe file

Coverage Input (required, mutually exclusive):
  --bam [FILE]          sorted bam file (ex: samtools sort input.bam -o sorted.bam)
  --cov [FILE]          coverage file [position coverage]

Output:
  -o [PATH], --outdir [PATH]
                        output directory
  -p [STR], --prefix [STR]
                        output prefix
```

## Test

```
cd tests
./runTest.sh
```

## Outputs 

-- prefix_amplicon_coverage.txt

| ID          | Whole_Amplicon | Unique  |
|-------------|----------------|---------|
| nCoV-2019_1 | 217.74         | 53.18   | 
| nCoV-2019_2 | 1552.83        | 1235.50 |
| nCoV-2019_3 | 3164.22        | 2831.73 |
| nCoV-2019_4 | 2005.16        | 1658.00 |
| etc...      |                |         |

#### Table Header Definition in the amplicon_coverage.txt 

<img width="465" alt="Screen Shot 2020-06-15 at 3 29 53 PM" src="https://user-images.githubusercontent.com/737589/84708117-1fc2e480-af1d-11ea-8411-35210a8dd6fa.png">

-- prefix_amplicon_coverage.html

```color black for < 5x and blue for <20x```

<a href="https://chienchi.github.io/amplicon_coverage_plot/index.html">![html](https://user-images.githubusercontent.com/737589/86061568-42c4bc80-ba24-11ea-93a1-0348e1dca930.png)</a>

