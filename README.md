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

This project was inspired by the dspipes ssh subsystem which is a part of the
Co:Z product by Dovetailed Technologies, http://dovetail.com. Depending on
what is wanted, use of the Co:Z code is likely to be a better decision that
using this code as a basis for your own custom code. Dovetailed Techologies
graciously allows use of their Co:Z product without a license fee. But, 
again unlike this code, they offer paid support if that is desired. I have
found them to be very fine people.

This code is _not_ designed to interoperate with Co:Z in any way. It is totally
of my own design and implementation. It is not supported by nor endorced by
Dovetailed Technologies. Use of this code is at your own risk.

