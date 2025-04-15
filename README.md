# CBT538
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. 
Due to amazing work by Alison Zhang and Jake Choi repos are no longer deleted.

```
//***FILE 538 is from Jan Jaeger and contains IPL text to IPL ZZSA, *   FILE 538
//*           which is his standalone editor.  This file is         *   FILE 538
//*           oriented to Hercules users, but can be adapted to     *   FILE 538
//*           conventional MVS as well.                             *   FILE 538
//*                                                                 *   FILE 538
//*             email:    jan.jaeger@westnet.com.au                 *   FILE 538
//*                                                                 *   FILE 538
//*       When run under Hercules on a PC, ZZSA is a tool to SEE    *   FILE 538
//*       MVS DASD and its contents, WITHOUT USING AN MVS SYSTEM!   *   FILE 538
//*                                                                 *   FILE 538
//*       - - - - - - - - N  O  T  E - - - - - - - - - - - - - -    *   FILE 538
//*                                                                 *   FILE 538
//*       If you are running Hercules already, you can use ZZSA     *   FILE 538
//*       immediately using a new member of this pds called         *   FILE 538
//*       ZZSAPACK.  ZZSAPACK is a zipped PC file which really      *   FILE 538
//*       is a Hercules, or PC/370 DASD minidisk.  You attach the   *   FILE 538
//*       ZZSA01 file to a Hercules configuration.  Then IPL it.    *   FILE 538
//*       You don't use MVS or z/OS, and you can see the contents   *   FILE 538
//*       of all the DASD in the configuration !!!  The ZZSA01      *   FILE 538
//*       pack is a mini-disk of ONLY ONE CYLINDER.  ZZSA is its    *   FILE 538
//*       IPL text.                                                 *   FILE 538
//*                                                                 *   FILE 538
//*       - - - - - - - - N  O  T  E  - - - - - - - - - - - - - -   *   FILE 538
//*                                                                 *   FILE 538
//*       This new member of this pds called ZZSAPACK was added     *   FILE 538
//*       by Sam Golob.  Download member ZZSAPACK, unzip it, and    *   FILE 538
//*       use it as a one-cylinder 3390 minidisk in a Hercules      *   FILE 538
//*       configuration.  IPL it, to run ZZSA and access all        *   FILE 538
//*       the MVS DASD in the configuration without IPL-ing         *   FILE 538
//*       another operating system.  Or you can attach the pack     *   FILE 538
//*       to a running Hercules configuration and IPL it.           *   FILE 538
//*                                                                 *   FILE 538
//*       Added members ZZSA80Z and ZZSA90Z which are newer         *   FILE 538
//*       versions of IPL-able ONE CYLINDER 3380 and 3390 packs,    *   FILE 538
//*       respectively, that will IPL ZZSA.  These contain this     *   FILE 538
//*       "help" information as dataset SYS1.ZZSA.HELP.  These      *   FILE 538
//*       two members are in zip format, but when you unzip them,   *   FILE 538
//*       they are usable in a Hercules configuration, and you      *   FILE 538
//*       can IPL ZZSA from them.  Remember that ZZSA80Z is a       *   FILE 538
//*       3380, and ZZSA90Z is a 3390.                              *   FILE 538
//*                                                                 *   FILE 538
//*       - - - - - - - - - - - - - - - - - - - - - - - - - - - -   *   FILE 538
//*                                                                 *   FILE 538
//*       Scenario to look at MVS DASD without MVS.  (Hercules      *   FILE 538
//*       has to be installed on the PC.)                           *   FILE 538
//*                                                                 *   FILE 538
//*       c:\hercules>         (Point to the Hercules executables)  *   FILE 538
//*                                                                 *   FILE 538
//*       Then start Hercules:                                      *   FILE 538
//*                                                                 *   FILE 538
//*       c:\hercules>hercules -f c:\hercconf\config.con            *   FILE 538
//*                                                                 *   FILE 538
//*       Now, in the Hercules window, add pack zzsa01 to the       *   FILE 538
//*       configuration using the attach command.                   *   FILE 538
//*                                                                 *   FILE 538
//*   Command ==> attach 0ab4 3390 c:\dasdtest\zzsa01               *   FILE 538
//*                                                                 *   FILE 538
//*   HHCDA020I c:\dasdtest\zzsa01 cyls=1 heads=15 tracks=15        *   FILE 538
//*                                                   trklen=56832  *   FILE 538
//*                                                                 *   FILE 538
//*       Then, in the Hercules window.....                         *   FILE 538
//*                                                                 *   FILE 538
//*       ipl ab4                                                   *   FILE 538
//*                                                                 *   FILE 538
//*       In your emulator window, where Hercules has started...    *   FILE 538
//*                                                                 *   FILE 538
//*       Type ESC to issue an interrupt, and ZZSA will prompt      *   FILE 538
//*       for a password.  The password is ZZSECRET.  Then you get  *   FILE 538
//*       the following introductory screen:                        *   FILE 538
//*                                                                 *   FILE 538
//*  ZZSAPRIM             Stand Alone Utilities                     *   FILE 538
//*                                                                 *   FILE 538
//*  Option ===>                                                    *   FILE 538
//*                                                                 *   FILE 538
//*      0 ListDev  - List all devices                              *   FILE 538
//*                                                                 *   FILE 538
//*      1 Browse   - Browse dataset or member                      *   FILE 538
//*                                                                 *   FILE 538
//*      2 Edit     - Edit dataset or member                        *   FILE 538
//*                                                                 *   FILE 538
//*      3 ListVTOC - List Volume Table of Contents                 *   FILE 538
//*                                                                 *   FILE 538
//*      4 ListPDS  - List PDS directory                            *   FILE 538
//*                                                                 *   FILE 538
//*      5 DispVol  - Display DASD volume label                     *   FILE 538
//*                                                                 *   FILE 538
//*      6 Dump     - Dump DASD record by CCHHR                     *   FILE 538
//*                                                                 *   FILE 538
//*      7 Zap      - Alter DASD record by CCHHR                    *   FILE 538
//*                                                                 *   FILE 538
//*      X Exit     - Terminate program                             *   FILE 538
//*                                                                 *   FILE 538
//*                                                                 *   FILE 538
//*      You should execute a "0" first, to list all the volumes    *   FILE 538
//*      in the configuration.  Afterward execute whatever other    *   FILE 538
//*      options you want to run.                                   *   FILE 538
//*                                                                 *   FILE 538
//*      From here, you can see what a versatile and useful DASD    *   FILE 538
//*      "look and change" program that ZZSA is.  It is entirely    *   FILE 538
//*      legal, as far as I know, to look at MVS or z/OS DASD       *   FILE 538
//*      using ZZSA, because ZZSA does not belong to IBM, and you   *   FILE 538
//*      have not IPL-ed an IBM operating system.                   *   FILE 538
//*                                                                 *   FILE 538
```
