# sbx_krakenhll

## Installation [KrakenHLL](https://github.com/fbreitwieser/krakenhll)🐙

  ```bash
  git clone https://github.com/fbreitwieser/krakenhll
  cd krakenhll
  bash install_krakenhll.sh $HOME/bin/
  export PATH=$PATH:$HOME/bin/
  ```
  
## Build KrakenHLL database for Bacteria complete genomes

  ```bash
  DBNAME=bacteriaDB
  krakenhll-download --db $DBNAME taxonomy
  krakenhll-download refseq/bacteria --db $DBNAME --dust --threads 8
  
  krakenhll-build -build --db $DBNAME --jellyfish-hash-size 6400M \
                --taxids-for-sequences --taxids-for-genomes --threads 8
  dump_taxdb taxDB taxonomy/names.dmp taxonomy/nodes.dmp
  ```

## Build KrakenHLL database for Virus all genomes

  ```bash
  DBNAME=virusAll
  krakenhll-download --db $DBNAME taxonomy
  krakenhll-download refseq/viral/Any --db $DBNAME --dust --threads 8
  krakenhll-download   viral-neighbors --db $DBNAME --dust --threads 8
  
  krakenhll-build -build --db $DBNAME --kmer-len 25 \
                --jellyfish-hash-size 6400M \
                --taxids-for-sequences --taxids-for-genomes --threads 8
  dump_taxdb taxDB taxonomy/names.dmp taxonomy/nodes.dmp
  ```

