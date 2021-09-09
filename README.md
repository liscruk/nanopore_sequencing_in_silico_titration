### nanopore_sequencing_in_silico_titration
In silico titration of optimal settings for nanopore basecalling on guppy using a Quadro RTX 5000.
This is a general trial and error benchmarking for basecalling since some settings are not entirely clearly explained or hard to find.

Some trials are documented here.

### Trials
I started with some basic settings and achieved in my opinion some nice results. But apparently improving was more difficult then expexted.

#### Trial 1
```
ONT Guppy basecalling software version 5.0.14+8f53ee955
config file:        /opt/ont/guppy/data/dna_r9.4.1_450bps_hac.cfg
model file:         /opt/ont/guppy/data/template_r9.4.1_450bps_hac.jsn
input path:         /fast5_test/
save path:          /test
chunk size:         1000
chunks per runner:  1000
minimum qscore:     7
records per file:   0
num basecallers:    1
gpu device:         cuda:0
kernel path:        
runners per device: 10
Found 11 fast5 files to process.
Init time: 971 ms

0%   10   20   30   40   50   60   70   80   90   100%
|----|----|----|----|----|----|----|----|----|----|
***************************************************
Caller time: 75861 ms, Samples called: 655797880, samples/s: 8.64473e+06
```
#### Trial 2
```
ONT Guppy basecalling software version 5.0.14+8f53ee955
config file:        /opt/ont/guppy/data/dna_r9.4.1_450bps_hac.cfg
model file:         /opt/ont/guppy/data/template_r9.4.1_450bps_hac.jsn
input path:         /fast5_test/
save path:          /test
chunk size:         1000
chunks per runner:  1000
minimum qscore:     7
records per file:   0
num basecallers:    1
gpu device:         cuda:0
kernel path:        
runners per device: 20
Found 11 fast5 files to process.
Init time: 1054 ms

0%   10   20   30   40   50   60   70   80   90   100%
|----|----|----|----|----|----|----|----|----|----|
***************************************************
Caller time: 73437 ms, Samples called: 655797880, samples/s: 8.93008e+06
Finishing up any open output files.
Basecalling completed successfully.
```
Trial 2 was the best one yet. However I have the feeling that memory is not optimally used and compute cores are currently the bottleneck.
It is however not obvious to me if there are settings to more effectively use memory while not overburdining the compute cores.
Since I have basecalling to perform for a project, I will for now use settings from the above trial and will expiriment more once I have time.

#### Trial 3
```
config file:        /opt/ont/guppy/data/dna_r9.4.1_450bps_hac.cfg
model file:         /opt/ont/guppy/data/template_r9.4.1_450bps_hac.jsn
input path:         /fast5_test/
save path:          /test
chunk size:         1000
chunks per runner:  1000
minimum qscore:     7
records per file:   0
num basecallers:    1
gpu device:         cuda:0
kernel path:        
runners per device: 50
Found 11 fast5 files to process.
Init time: 1600 ms

0%   10   20   30   40   50   60   70   80   90   100%
|----|----|----|----|----|----|----|----|----|----|
***************************************************
Caller time: 74322 ms, Samples called: 655797880, samples/s: 8.82374e+06
Finishing up any open output files.
Basecalling completed successfully.
```
#### Trial 4
```
ONT Guppy basecalling software version 5.0.14+8f53ee955
config file:        /opt/ont/guppy/data/dna_r9.4.1_450bps_hac.cfg
model file:         /opt/ont/guppy/data/template_r9.4.1_450bps_hac.jsn
input path:         /fast5_test/
save path:          /test
chunk size:         1000
chunks per runner:  1000
minimum qscore:     7
records per file:   0
num basecallers:    1
gpu device:         cuda:0
kernel path:        
runners per device: 40
Found 11 fast5 files to process.
Init time: 1327 ms

0%   10   20   30   40   50   60   70   80   90   100%
|----|----|----|----|----|----|----|----|----|----|
***************************************************
Caller time: 73665 ms, Samples called: 655797880, samples/s: 8.90244e+06
Finishing up any open output files.
Basecalling completed successfully.

```

