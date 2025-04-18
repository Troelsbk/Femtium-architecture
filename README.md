## The Femtium architecture 
#### This is the write-up for the binexp1 challenge in the Danish Defence Intelligence Service requirement campaign for the newly announced Hacker Academy [Hackerakademiet]. 
##### For more info see [Version2].

We are given a binary (binexp1) file written for the fictive Femtium architecture. 
Since no tools are available to analyse this file format, we have to contruct our own Femtium CPU from the given instruction set.

To sum up the program does the following:
- Writes "Password:" to stdout.
- Recieves a password of 24 exactly chr., no more no less.
- Stores a string in memory (the reference).
- Stores a second string memory.
- Checks length of password.
- Does some arithmetic with the first 1/3 password and the first 1/3 second string.
![first](https://i.ibb.co/Dfh7Sft/first-part.jpg)
- Uses five NOR instuction to XOR the 2/3 part of the password with the 2/3 of the second string. 
![second](https://i.ibb.co/BZt7DV8/second-part.jpg)
- For the last 1/3 some arithmetic are done again.
![second](https://i.ibb.co/510ZkKV/third-part.jpg)
- Compare the reference string with some unresolved/unwritten address at 0x4b8
![compare](https://i.ibb.co/xCtJw0z/compare.jpg)
- Write "Nope!" to sdtout or write "you did it" to stdout dependent on whether or not the reference string is located at 0x4b8.

Solution:
We have to combine the second string with some input string (the flag?) to yield the reference string. 

## binexp_vm.py 
My partial implementaion of the Virtual machine for Femtium file, since only instructions needed to complite the challange are implemented.
## Femtium_assamble.asm
Femtium assemble with comments. It contains assemble from two runs. 
- One full print of instructions with no reference string stored in memory at 0x4b8 which return the "nope". 
- Located at the bottom, is a partial print from a second run, with the reference string artificially written to memory location 0x4b8 which returns "you did it!". 

## instructions.md
Femtium Instruction Reference. Contain Instruction Format, Field reference ect. 

## binexp1
The original Femtium file from the challange

## binexp_functions.py
My solution the challange. 
The flag is printed in the end.

# Summary
Overall, a very fun exercise. A few months later, a mug arrived in the mail as a reward for completing the challenge. 
This exercise was by far the most interesting in the set and was in line with the earlier challenge presented back in [2017].



 

[Hackerakademiet]: https://hackerakademi.dk
[Version2]: https://www.version2.dk/artikel/forsvaret-er-paa-jagt-efter-hackere-til-specialenhed
[2017]: https://github.com/RobertLarsen/FE-2017
