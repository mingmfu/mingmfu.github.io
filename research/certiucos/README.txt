# A Practical Verification Framework for Preemptive OS Kernels

This is the artifact for the CAV 2016 paper:
"A Practical Verification Framework for Preemptive OS Kernels".

-------------------------------------------------------------------------

## Virtual Machine

- ID / Password: "cav" / "ae". The ID has `sudo` privileges.

- All contents are in `/home/cav/coqimp/`:

  + `CertiOS/` : the Coq package without compilation

  + `CertiOS_Compiled/` : the Coq package compiled with Coq8.4pl6

  +  paper.pdf : our accepted paper

  +  paper-tr.pdf : the extended version of our accepted paper

  +  README.txt

-------------------------------------------------------------------------

## Contents

A.`framework/`: the verification framework

   a)`machine/`: modeling of the kernel (corresponding to Section 3
      of the paper)

      (i)`memory/`: the C memory model

      (ii)`language.v`: the low-level language for a practical
      subset of C, and the high-level specification language
      (corresponding to Sections 3.1 and 3.2 of the paper)

      (iii)`opsem.v`: the operational semantics for the low-level
      and high-level languages

   b)`logic/`: relational program logic for refinement verification
   (corresponding to Section 4 of the paper)

       (i)`assertion.v`: the assertion language

       (ii)`inferules.v`: the inference rules

       (iii)`soundness.v`: the soundness proofs of the inference rules

   c)`simulation/simulation.v`: definitions of compositional simulation
   relations, which are employed as the underlying semantics for proving
   the soundness of the program logic

   d)`theory/`: OS correctness definition and auxiliary
   compositionality lemmas

        (i)`toptheorem.v`: OS correctness definition
        (corresponding to Section 3.3) and some auxiliary lemmas for
        proving the soundness of the verification framework

        (ii)`lemmasfortoptheo.v` : the auxiliary lemmas for proving
	    the lemmas in `toptheorem.v`

   e)`auxlibs/`: auxiliary definitions and lemmas for proving the
   soundness of the program logic

   f)`toprule.v`: the top rule and the soundness theorem of the
   verification framework (corresponding to Theorem 4.1 in the paper)

B.`tactics/`: automated tactics provided by the verification framework

   a)`derivedrules.v`: derived inference rules based on "inferules.v"
   for developing automated tactics

   b)`aux_for_hoare_lemmas.v` & `hoare_assign.v` & `hoare_conseq.v` &
   `hoare_lemmas.v` & `hoare_tactics.v` & `symbolic_execution.v` :
   the coq files for the tactic "hoare forward", which is used to
   automatically generate verification conditions

   c)`lemmasforseplog.v` & `seplog_lemmas.v` & `seplog_tactics.v` &
   `tacticsforseplog.v` : the coq files for the tactic "sep auto"
   and its variations, which are used to prove entailments of
   relational assertions

   d)`IntLib.v` & `mathsolver.v` : the coq files for tactics "int auto"
   and "mauto", which are used to automatically prove the mathematical
   properties of machine integers involved with bit operations

C.`certiucos/`: verifying uC/OS-II with the refinement program
   logic and proving priority-inversion-freedom (PIF) for mutexes
   in uC/OS-II (corresponding to Sections 6 and 5, respectively)

   a)`code/`: notations, macros, Coq definitions for the C code of
   the key modules of uC/OS-II, which are manually defined in Coq
   following the original C source code (see D below).

   b)`spec/`: the specifications for uC/OS-II code and the PIF
      property

       (i)`OSQInvDef.v` & `OSTCBInvDef.v` : global invariants for
       specifying the shared resources between interrupt handlers
       and non-handler code

       (ii)`absop.v` : the specification code written with our
       specification language for specifying kernel APIs and
       interrupt handlers of uC/OS-II

       (iii)`InternalFunSpec.v` : specifications of internal functions

       (iv)`absop_rules.v` : abstract implication rules of abstract
       operations

       (v)`PIF_def.v` : the definition of PIF

       (vi)`PIF_aux.v` : some auxiliary definitions and lemmas for
       proving PIF

   c)`proofs/`: refinement proofs for internal functions, APIs and
   interrupts

   d)`ucos_lib/`: libraries for common properties of bitmaps,
   auxiliary lemmas for functional properties of uC/OS-II

   e)`ucos_correct.v`: two correctness theorems, 
   one is for the correctness of APIs (as contextual refinement) of 
   uC/OS-II which is instantiated with Def.3.1, and the other is for 
   PIF of mutexes in uC/OS-II (corresponding to Theorem 5.2 in the paper) 

D.`ucosII-v2.52.zip`: the original C source code of an earlier
   version (V2.52) of uC/OS-II, which is obtained from the companion
   CD-ROM of the book "MicroC OS II: The Real Time Kernel
   (with CD-ROM) 2nd Edition"

-------------------------------------------------------------------------

## Notes

A. The entire package is successfully compiled with Coq 8.4pl6 on a
   machine with 3.6GHz cpu and *32G* memory plus 4G swap.

   Before compiling the package in the virtual machine provided by us,
   you need to reconfigure the virtual machine by assigning enough
   memory to it.

   For example, if your computer has 32G memory, you can assign 28G
   memory and set up 15G swap for the virtual machine by following
   the steps below:
   (1) setting -> system, adjust the memory space of the virtual
       machine to 28G
   (2) setting -> storage -> Controller:SATA
      (a) create a new virtual disk image (VDI) with the size of 15G
      (b) add the new VDI to your virtual machine, then you can see
          two disks
   (3) start the virtual machine and type the following commands to
   set the 15G VDI as your swap:

   `sudo mkswap /dev/sdb`
   `sudo swapon /dev/sdb`

   Now if you type `free -l` to check the free space, you will see
   28G memory & 17G swap in your system, which are large enough for
   compiling the entire Coq package. Note that using swap may slow
   down the compilation procedure, thus please try to assign memory
   to the virtual machine as much as you can.

   Then the compilation can be reproduced in the virtual machine with
   the following commands:

   a) If you only want to compile the soundness theorem of the
   verification framework, please type the following commands:

   `cd /home/cav/coqimp/CertiOS`
   `make framework/toprule.vo`

   Note this command compiles the verification framework *only* and
   it does NOT compile the specifications and proofs for uC/OS-II.
   On the aforementioned machine (3.6GHz cpu and *32G* memory plus
   4G swap), the compilation takes around half an hour.

   b) If you want to compile the correctness theorem for uC/OS-II,
   please type the following commands:

   `cd /home/cav/coqimp/CertiOS`
   `make certiucos/ucos_correct.vo`

   This command compiles the *entire* package. On the aforementioned
   machine, it takes around 16 hours to finish the compilation.

   c) If you want to count the lines of Coq code, please type
   the following commands:

   `cd /home/cav/coqimp/CertiOS`
   `make framework-wc`  (the top left corner in Table.1 of our paper)
   `make ucoslib-wc`    (the bottom left corner in Table.1 of our paper)
   `make ucosproof-wc`  (the right column in Table.1 of our paper)

   Note that we did some minor modifications to the original submission
   of the Coq code to make it more readable and clean, therefore the
   numbers generated by the above commands have small differences
   comparing to the original numbers in Table 1.

B. Since the compilation takes really long time (16 hours for the
   entire package or half an hour for the verification framework
   only, on the aforementioned machine), we also provide pre-compiled
   files (together with source) in the following directory:

   	      	`/home/cav/coqimp/CertiOS_Compiled/`.

C. You can use the following command to open individual Coq source
   files using emacs and ProofGeneral:

     	       	    	 `sh pg XXX.v`

   If the source file is from the pre-compiled package (see B above),
   you could go through the proof scripts directly in emacs.
   Otherwise (if it is from the directory containing source code only),
   you have to compile the package yourself following the instructions
   given in A above.
