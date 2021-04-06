---
layout: post
title: "Verifying a VSAM file"
date: "2004-06-04"
tags: 
  - "mainframes"
---

When a VSAM file is opened by a job in the output mode, a flag in the VSAM catalog called "open-for-output" gets set to 'ON'. This flag does not get turned off until the job ends successfully i.e. until the job closes the file normally. Or in case we are editing the file manually in file-aid, the flag gets set when we open the file and gets turned off when we close it. But say the job goes down halfway through the update process or our TSO session expires before we could close the file. The "open-for-output" flag remains turned on. What happens to the file now?

When next time a job/user tries to open the file for output, the file manager trots off to the catalog to turn on the flag. But the flag is already on!! So it guesses (somewhat optimistically) that some other job might have opened the file. It issues a GRS (Global resource serialization) enqueueing on the file to find that out. If the file is not open anywhere else, it comes to know that it was not closed properly during its last use and its time for some catalog cleanup. Enter VERIFY.

Verify is a record management macro like get or put. In our case, the open processing issues an implicit verify against the file. This can be confirmed by the IEC161I type warning messages (RC of 56 and 62) in the sysout. The verify macro will compare the ICF catalog information with the physical VSAM cluster. It starts reading the VSAM dataset CI by CI, starting with the High Used RBA. It compares HURBA value, number of index levels, system time-stamp and many other fields. If the verify is not successful, it will issue a warning message with a return code of 116 (X'74'). Two things worth noting about implicit verify macro:

1. It will _not_ correct the catalog information. That is the job reserved for IDCAMS verify. It will just issue some warning messages. It is up to us to figure out what to do next. We can continue processing but the data integrity won't be guaranteed.
2. Implicit verify is not issued if the file is being opened for input or reset processing. Or if the VSAM file is of type LDS.

IDCAMS verify is an explicit verify command. When an IDCAMS verify is issued against a file, it opens the file, calls the record management verify macro and then closes the file. And it is at the time of closing the file that the ICF catalog gets updated and the "open-for-output" flag gets reset. Two things worth noting about explicit verify macro:

1. A successful verify does _not_ guarantee that everything is fine now. The catalog statistics may be invalid; the file might have duplicate or missing records. HURBA may be off by a few bytes.
2. IDCAMS verify does not update the catalog or the VSAM control blocks directly. It relies on the implicit verify and VSAM close processing to do its job.

So whether the verify is successful or not, the structural integrity of a VSAM file is not guaranteed. Its always a good idea to take standard recovery actions on such files.
