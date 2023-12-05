# CAN-Verify

---

## Description

The aim of this program is to translate CAN code to BigraphER code and run BigraphER and PRISM for verification.  
It was developped by Thibault Rivoalen ([thibault.rivoalen@alumni.enac.fr](mailto:thibault.rivoalen@alumni.enac.fr)) for the University of Glasgow, UK.

---

## Building the program

### With Docker for a standalone version

Run ```make docker``` to have a ```can-verify``` Docker image built  

### Without Docker for a faster version

To build the project and have an executable ```CAN-Verify``` (promoted to the root folder), run : ``` make ```  
A documentation will also be build during the process.

#### Dependencies
Java 17 (or above), PRISM model checker in the PATH  
Opam/OCaml, dune, dune-configurator, jsonm, menhir, cmdliner, ppx_optcomp, mtime, zarith, odoc, BigraphER in the PATH

---

## Usage

### With Docker
Run the program with your current directory files with 
```
docker run --rm --volume "${PWD}":/test_rep --interactive can-verify [options] <file.can>
```

### Without Docker
Run ```./CAN-Verify  [options] <file.can>```

### Options

```-static```: to perform a static check of ```file.can```  
```-dynamic```: to perform a dynamic check with BigraphER and PRISM   
```-p```: to tell the program which file contains the properties to verify  
```-Ms```: to tell the maximum number of states possible (default: 4000)  
```-mp```: to tell the minimum number of plan required (default: 2)  
```-Mp```: to tell the maximum number of plan allowed (default: 100)  
```-mc```: to tell the minimum number of character required in a name (default: 2)  
```-Mc```: to tell the maximum number of character allowed in a name (default: 20)

## Copyright and license
Copyright 2012-2022 Glasgow Bigraph Team  
All rights reserved. Tools distributed under the terms of the Simplified BSD License that can be found in the [LICENSE file](LICENSE.md).