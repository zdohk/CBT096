~~~~~~~~~~~~~~~~

//***FILE 096 CONTAINS SEVERAL UTILITIES AND SYSTEM EXITS USED AT   *   FILE 096
//*           THE UNIVERSITY OF MISSOURI HOSPITAL AND CLINICS OF    *   FILE 096
//*           COLUMBUS, MISSOURI.                                   *   FILE 096
//*                                                                 *   FILE 096
//*           THE FOLLOWING UTILITIES ARE INCLUDED IN THIS DATASET  *   FILE 096
//*           (NOTE IF THE FIRST CHARACTER OF THE MEMBER IS "=" IT  *   FILE 096
//*            IS REALLY AN AT-SIGN)                                *   FILE 096
//*                                                                 *   FILE 096
//*             ***** DASD ALLOCATION/RENAME CONTROL *****          *   FILE 096
//*                                                                 *   FILE 096
//*           HCCDADSM - EXIT TO RESTRICT DASD DATASET ALLOCATIONS  *   FILE 096
//*                      BY DSNAME, VOLUME, AND USER RACF           *   FILE 096
//*                      AUTHORITY.                                 *   FILE 096
//*           IGGPRE00 - DADSM EXIT TO CONDITIONALLY LINK TO        *   FILE 096
//*                      HCCDADSM ONLY IF IT IS PRESENT.            *   FILE 096
//*           INIDADSM - PROGRAM TO PROCESS PARAMETERS AND SETUP    *   FILE 096
//*                      HCCDADSM CONTROL BLOCK (DADSMBLK)          *   FILE 096
//*           INITNCT  - PROGRAM TO BUILD USER CVT (WE CALL THIS    *   FILE 096
//*                      CONTROL BLOCK THE NETWORK CONTROL TABLE    *   FILE 096
//*                      OR NCT) AND PLACE ITS ADDRESS IN THE       *   FILE 096
//*                      CVTUSER FIELD.  THIS CONTROL BLOCK IS      *   FILE 096
//*                      USED AS THE ANCHOR FOR THE DADSMBLK        *   FILE 096
//*                      ABOVE.                                     *   FILE 096
//*           IPLDATE  - TSO CP TO EXTRACT AND FORMAT THE LAST IPL  *   FILE 096
//*                      DATE AND TIME FROM THE NCT (SINCE THE NCT  *   FILE 096
//*                      IS CREATED FAIRLY LATE IN THE IPL, THIS    *   FILE 096
//*                      IS A BETTER APPROXIMATION OF THE ACTUAL    *   FILE 096
//*                      "SYSTEM AVAILABLE" DATE AND TIME THAN      *   FILE 096
//*                      THAT IN THE SMCA).                         *   FILE 096
//*           DADSMMOD - TSO CP TO ALLOW AUTHORIZED USERS TO        *   FILE 096
//*                      TEMPORARILY MODIFY DADSM PROTECTION        *   FILE 096
//*                      ATTRIBUTES IN DADSMBLK.                    *   FILE 096
//*           =DADSMMD - TSO HELP FOR DADSMMOD COMMAND.             *   FILE 096
//*           =INIDASD - SAMPLE INITIALIZATION PARAMETERS FOR       *   FILE 096
//*                      INIDADSM ABOVE.                            *   FILE 096
//*           =DADSM   - SAMPLE JCL FOR DADSM STARTED TASK TO SET   *   FILE 096
//*                      UP DADSMBLK.                               *   FILE 096
//*           =INITSYS - SAMPLE JCL FOR INITSYS STARTED TASK TO     *   FILE 096
//*                      SET UP NCT.                                *   FILE 096
//*           =NCTDOC  - GENERAL COMMENTS ABOUT THE NCT, WHEN/HOW   *   FILE 096
//*                      IT IS CREATED, ETC.                        *   FILE 096
//*                                                                 *   FILE 096
//*             ***** RETURN CODE CHECKER *****                     *   FILE 096
//*                                                                 *   FILE 096
//*           HCCRCCK  - PROGRAM TO FORCE AN ABEND ON A BAD RETURN  *   FILE 096
//*                      CODE, ALLOWING CONDITIONAL DISP TO BE      *   FILE 096
//*                      TAKEN FOR DATA SETS.                       *   FILE 096
//*           ATTCHATH - ATTACH/REAUTH SUBROUTINE USED BY HCCRCCK.  *   FILE 096
//*           =HCCRCCK - SAMPLE JCL FOR EXECUTING THE HCCRCCK       *   FILE 096
//*                      PROGRAM.                                   *   FILE 096
//*                                                                 *   FILE 096
//*             ***** JES2 CHECKPOINT PERFORMANCE MONITOR ****      *   FILE 096
//*                                                                 *   FILE 096
//*           HJUX2530 - SAMPLE JES EXIT 253 TO CUT SMF RECORDS     *   FILE 096
//*                      FOR JES2 CHECKPOINT PERFORMANCE            *   FILE 096
//*                      MONITORING.                                *   FILE 096
//*           TSJESSMF - PL/1 PROGRAM TO REDUCE AND ANALYZE SMF     *   FILE 096
//*                      RECORDS PRODUCED BY HJUX2530 ABOVE.        *   FILE 096
//*           PDUMP    - SUBROUTINE FOR TSJESSMF (PL/1 DATA AREA    *   FILE 096
//*                      FORMATTED DUMP)                            *   FILE 096
//*           =JESSMF  - SAMPLE JCL TO EXECUTE THE TSJESSMF         *   FILE 096
//*                      PROGRAM.                                   *   FILE 096
//*           =JESPARM - SAMPLE JES2 INITIALIZATION PARAMETERS FOR  *   FILE 096
//*                      HJUX2530.                                  *   FILE 096
//*           =JESCKPT - VARIOUS STUFF ABOUT JES2 CHECKPOINT        *   FILE 096
//*                      PROCESSING                                 *   FILE 096
//*                                                                 *   FILE 096
//*             ***** JCL PRESCAN AND REPLACEMENT ****              *   FILE 096
//*                                                                 *   FILE 096
//*           IEFUJV   - SMF EXIT TO SCAN AND CONDITIONALLY         *   FILE 096
//*                      REPLACE CERTAIN SYMBOLIC PARAMETERS IN     *   FILE 096
//*                      JCL PRIOR TO CONVERSION (E.G., HOST NAME,  *   FILE 096
//*                      DAY OF WEEK, DATE, ETC. CAN BE PLACED IN   *   FILE 096
//*                      APPROPRIATE PLACES IN YOUR JCL PRIOR TO    *   FILE 096
//*                      CONVERSION).                               *   FILE 096
//*           =IEFUJV  - INSTRUCTIONS FOR USING IEFUJV MODULE AS    *   FILE 096
//*                      SHIPPED.                                   *   FILE 096
//*                                                                 *   FILE 096
//*             ***** VARIOUS PL/1 STUFF ****                       *   FILE 096
//*                                                                 *   FILE 096
//*           PLIARRV  - MACRO TO GENERATE PL/1 STANDARD ENTRY      *   FILE 096
//*                      POINT TO ASSEMBLY LANGUAGE SUBROUTINES.    *   FILE 096
//*           PLIRETN  - MACRO TO GENERATE PL/1 STANDARD RETURN     *   FILE 096
//*                      SEQUENCE FOR ASSEMBLY LANGUAGE             *   FILE 096
//*                      SUBROUTINES.                               *   FILE 096
//*           DSAD     - MACRO TO GENERATE A DSECT DESCRIBING THE   *   FILE 096
//*                      PL/1 DYNAMIC STORAGE AREA (DSA).           *   FILE 096
//*           TRIM     - ASSEMBLY LANGUAGE SUBROUTINE TO CHOP       *   FILE 096
//*                      LEADING AND TRAILING BLANKS FROM A         *   FILE 096
//*                      CHARACTER STRING.                          *   FILE 096
//*           FINDCHR  - ASSEMBLY LANGUAGE SUBROUTINE TO LOCATE     *   FILE 096
//*                      THE FIRST CHARACTER IN A STRING MATCHING   *   FILE 096
//*                      ANY CHARACTER IN AN INDEX STRING.          *   FILE 096
//*                                                                 *   FILE 096
//*             ***** SMP/E SUPPORT FOR ABOVE FUNCTIONS ****        *   FILE 096
//*                                                                 *   FILE 096
//*           MDL0101  - SMP/E USERMOD TO INSTALL                   *   FILE 096
//*                      HCCDADSM/IGGPRE00 INTO YOUR (MVS/SP        *   FILE 096
//*                      1.3.6) SYSTEM.                             *   FILE 096
//*           MDL0103  - SMP/E USERMOD TO INSTALL                   *   FILE 096
//*                      HCCDADSM/IGGPRE00 INTO YOUR (MVS/SP 2.2)   *   FILE 096
//*                      SYSTEM.                                    *   FILE 096
//*           MJL1401  - SMP/E USERMOD TO INSTALL EXIT POINTS FOR   *   FILE 096
//*                      EXIT 253 INTO YOUR JES2 (1.3.6) HASPCKPT   *   FILE 096
//*                      MODULE.                                    *   FILE 096
//*           MJL1501  - SMP/E USERMOD TO ADD KNOWLEDGE OF          *   FILE 096
//*                      HJUX2530 (EXIT 253) TO YOUR JES2 (1.3.6)   *   FILE 096
//*                      SYSTEM.                                    *   FILE 096
//*           MSL0101  - SMP/E USERMOD TO ADD KNOWLEDGE OF IEFUJV   *   FILE 096
//*                      INTO YOUR MVS (1.3.6) SYSTEM.              *   FILE 096
//*           MSL0103  - SMP/E USERMOD TO ADD KNOWLEDGE OF IEFUJV   *   FILE 096
//*                      INTO YOUR MVS (2.2) SYSTEM.                *   FILE 096
//*                                                                 *   FILE 096
//*                                                                 *   FILE 096
~~~~~~~~~~~~~~~~

