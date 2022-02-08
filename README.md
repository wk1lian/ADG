# ADG
Universal clustering algorithm based on an adaptive density gradient

## HELP
```
Version: 1.0
License: GPL-3.0
Required: Java8 or later

Usage: java -jar [thisjar] [model] [Options]
  e.g. 1 | java -jar [thisjar] sort -t=0 -i=yourDataFile -h=true -s=\t -k=10 -m=200 -c=80
  e.g. 2 | java -jar [thisjar] sort -t=0 -i=yourDataFile -h=true -s=\t -k=10,15,20 -m=200
  e.g. 3 | java -jar [thisjar] sort -t=1 -i=yourDataFile -k=10,15,20 -m=200 -n=10
  e.g. 4 | java -jar [thisjar] sort -t=5000 -i=yourDataFile -m=200 -n=10
  e.g. 5 | java -jar [thisjar] -i=yourDataFile -m=200 -n=10

Model:
  raw/sort: See differences in our publication. Default: sort.
Options:
  -c=Obtaining the core clusters by labeling a certain proportion of edge samples as atypical samples for each cluster.
    eg. 80 means 80%, default: 50
  -d=The delimiter of the input data, default: \t
  -H=Whether the data contains a header, boolean, default: true
  -i=Input file, required. See -t for data Types.
  -k=The number of nearest neighbors to be considered to get the cutoff distance of each sample, positive integer(s).
    In sort mode, multiple values can be received (comma-separated) and multiple results will be output.
    default: 10
  -m=The minimum number of samples required to generate a new cluster.
    (usually less than the number of samples of the expected smallest cluster),
    default: 200
  -n=Expected number of clusters, positive integer
    If specified, in addition to the specified k and m, clustering will be performed by changing k until (not guaranteed) the expected number of clusters are obtained.
  -o=Output path, default: the same path as the input file. The output file is named yourInputName_k_m.csv
  -s=Whether to save the distance matrix, default: 0
    0: not save
    1: save the distance matrix
    2: save the sorted distance vectors (only in sort model)
  -t=The type of data, positive integer, default: 0
    0: sample features, separated by a delimiter
    1: complete distance matrix, separated by a delimiter
    2: sorted vectors, separated by a delimiter
    other positive integer(x): trigonometric distance matrix, one row for each value, x represents the sample size
  -T=The number of threads used to sort the distance vectors, only applies to sort model, default: 1
-h, --help
  Print this help

Output format:
  Three columns will be output for each k.
  eg. parameters: sort k=10,15; m=200; c=80
    output header:
      10_200_9    10_200_9_80%    10_200_9_order    15_200_6    15_200_6_80%    15_200_6_order
    explain:
      10_200_9 means the raw clusters for k=10, m=200. The number of clusters=9
      10_200_9_80% means the 80% core clusters for k=10, m=200
      10_299_9_order means the order in which the samples are added to the clusters for k=10, m=200
      10_200_9 means the raw clusters for k=15, m=200. The number of clusters=6
      10_200_9_80% means the 80% core clusters for k=15, m=200
      10_299_9_order means the order in which the samples are added to the clusters for k=15, m=200
```
