
It can be tedious to repeatedly type input to the programs you are testing. Most operating systems support file redirection, which lets us associate a named file with the standard input and the standard output:
```
$ addItems <infile >outfile
```

this command will read transactions from a file named `infile` and write its output to a file named `outfile` in the current directory.