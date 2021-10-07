# API Overview

The ChronoScan Capture API allows to access ChronoScan Jobs&Batches from any
dev platform that supports automation, like VBScript, Visual Basic or C#.

Any API client must have a working ChronoScan installation.

- [CSAClient](./objects/CSAClient) is the main object on this API, it gives access to a ChronoScan configuration, and  allows to load Jobs and create other objects.
- [ChronoCMD](./ChronoCMD) is a command line access utility to process files and execute common tasks.

## Running external programs with ChronoScan

### Notes
* Your executable must be run on the same directory than ChronoScan: __"%programfiles(x86)%\ChronoScan\Bin"__ directory.
* ChronoScan API clients MUST be run on the same directory that you ChronoScan installation.
