# Install dependencies

The first step is to install depndencies:

1. Install GGplot2

```
install.packages("ggplot2")
```

2. Install iterators

```
install.packages("iterators")
```

3. Grid extra

```
install.packages("gridExtra")
install.packages("ggplotFL", repos="http://flr-project.org/R", INSTALL_opts = c("--with-keep.source"))
```

3. Install FLCore

```
install.packages("FLCore", repos="http://flr-project.org/R", INSTALL_opts = c("--with-keep.source"))
```

3. FLBRP

```
install.packages("FLBRP", repos="http:///flr-project.org/R", INSTALL_opts = c("--with-keep.source"))
```

4. FLife
```
install.packages("FLife", repos="http:///flr-project.org/R", INSTALL_opts = c("--with-keep.source"))
```

5. FLife
```
install.packages("FLasher", repos="http://flr-project.org/R", INSTALL_opts = c("--with-keep.source"))
```

# Debug packages

1. Download the git repository for the source code of the package you want to install to a separate directory.
2. Modify your ~/.r/Makevars file and include the following

```
 R_INSTALL_STAGED = false
 ALL_CXXFLAGS = -ggdb -O0 -Wall
 ALL_CFLAGS = -ggdb -O0 -Wall
```
3. Install package in R, which will compile the code

```bash
R
```

```R
install.packages('/absolute/path/to/package', repos=NULL, verbose = TRUE, quiet = FALSE)
```

If your package was previously installed and compiled and need to reinstall/recompile, then remove the respective directory on cd /usr/local/Cellar/r/4.0.0_1/lib/R/library/

4. Start R in debug mode

```bash
R --debugger=lldb
```

5. Optional set breakpoints


```lldb
breakpoint set --name FunctionName
```

6. Run debug process 

```lldb
run
```


## Scenarios

* Life history: SP, DE, LP
		* SP Small Pelagic: Linf=30cm, ages=1:8, fbar=2:8, steep=0.7
		* DE Demersal: Linf=100cm, ages=1:20, fbar=4:20, steep=0.6
		* LP Large Pelagic: Linf=250cm, ages=1:30, fbar=6:30, steep=0.85
* Initial depletion: ID10, ID40, ID60
* Effort/F dynamics, x value: ED0.1, ED0.3, ED0.6, FD
* Selectivity: SELFD, SELF, SELD, SELDF
* Length of time series: TS20, TS40, TS60
* Under-reporting catch %: UR0, UR10, UR25, UR50

##



## out list
* lh: FLPar, output of call to gislasim()
* code: simulation code, see table above
* stock: FLStock
* refpts: FLPar, FLBRP refpts of original object by lh()
* val: data.frame, values of variables in scenarios table



# ADD other effort dynamics

- One way trip: exponential to 0.80 Fcrash

- Up to 0.80 Fcrash, growing by 20%/year, then stay at 0.80Fcrash for 4 years, and then down to FMSY by 15%/year

- CONTRAST in time series

- Catch ERROR, 20% CV rlnorm

# GRID

- LH (3) SP, DE, LP
- AR (2) NR, AR
- ID (3) ID0, ID30, ID60
- ED (4) ED0, ED0.6, OW, RC
- TS (2) TS20, TS60
- UR (2) UR0, UR50

