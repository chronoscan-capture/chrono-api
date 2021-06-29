# API Overview

The ChronoScan Capture API allows to access ChronoScan Jobs&Batches from any
dev platform that supports automation, like VBScript, Visual Basic or C#.

Any API client must have a working ChronoScan installation.

**CSAClient** is the main object on this API, it gives access to a ChronoScan configuration, and
allows to load Jobs and create other objects.

## Running external programs with ChronoScan

### Notes
* ChronoScan API clients MUST be run on the same directory that you ChronoScan installation.
* Compile or install your executable on your __"%programfiles(x86)%\ChronoScan\Bin"__ directory.

