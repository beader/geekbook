# R

### openblas


```zsh
sudo apt-get install gcc gfortran libreadline-dev

cd R-3.2.3
./configure --enable-R-shlib --enable-BLAS-shlib --enable-memory-profiling --with-tcltk=no
sudo checkinstall
```
