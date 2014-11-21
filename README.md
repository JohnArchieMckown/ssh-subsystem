ssh-subsystem
=============
This repository contains my code for an ssh subsystem. It is designed around
the z/OS port of OpenSSH by IBM. One reason to use a subsystem, instead of 
doing a plain ssh is because the z/OS system is EBCDIC based. So the standard
ssh tunnel automatically performs a code translation between ASCII and EBCDIC.
Most of the time, this is what is wanted. But there are occasions where it 
is a bother. By using an ssh subsystem, this translation is avoided which lets
the invoked z/OS UNIX program decided if, and how, any input or output is 
translated. 

Inspirition
-----------
This project was inspired by the dspipes ssh subsystem which is a part of the
Co:Z product by Dovetailed Technologies, http://dovetail.com. Depending on
what is wanted, use of the Co:Z code is likely to be a better decision that
using this code as a basis for your own custom code. Dovetailed Techologies
graciously allows use of their Co:Z product without a license fee. But, 
again unlike this code, they offer paid support if that is desired. I have
found them to be very fine people.

Disclaimer
----------
This code is _not_ designed to interoperate with Co:Z in any way. It is totally
of my own design and implementation. It is not supported by nor endorced by
Dovetailed Technologies. Use of this code is at your own risk.

Functions
---------

Functions, in this case, means the programs which implement or use the ssh 
subsystem or subsystems. This list includes implemented, in-progress, and 
desired functions. This list will be revised periodically. In no case is 
it to be taken as a promise that any particular function will actually be
implemented or even retained on the list in the future.

### binexec
binexec is a program which is used as an ssh subsystem. It needs to be installed
in a directory accessable to the ssh daemon. It's entire purpose in life is to
find and exec() the program requested by the client. The client may request that
_any_ UNIX program be run. The program can be specified with an absolute path to
the executable. Or it can be a relative path. If it is a relative path, then the
directories in the PATH environment variable will be searched, in order, for 
the specified program. If it is either not found or not executable by the requesting
user, an error is returned. If it is found and is executable by the requestor,
then the program is simply invoked using the BPX1EXC system service. The program
is written in HLASM. This function does not do any code conversion. The requested
program is responsible for any required code conversion.

### binexec2
binexec2 is functionally identical to binexec. The only difference is that it is
written in C instead of HLASM and uses the C standard execvp() function to find
and execute the specified program. 


