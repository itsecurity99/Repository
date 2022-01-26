VOLATILITY CHEATSHEET
Below are some of the more commonly used plugins from Volatility 2 and their Volatility 3 counterparts.

OS INFORMATION
IMAGEINFO

Volatility 2
Volatility 3

vol.py -f “/path/to/file” imageinfo

vol.py -f “/path/to/file” kdbgscan



Output differences:
- Volatility 2: Additional information can be gathered with kdbgscan if an appropriate profile wasn’t found with imageinfo
- Volatility 3: Includes x32/x64 determination, major and minor OS versions, and kdbg information

Note: This applies for this specific command, but also all others below, Volatility 3 was significantly faster in returning the requested information



PROCESS INFORMATION
PSLIST

Volatility 2
Volatility 3

vol.py -f “/path/to/file” ‑‑profile <profile> pslist

vol.py -f “/path/to/file” ‑‑profile <profile> psscan

vol.py -f “/path/to/file” ‑‑profile <profile> pstree

vol.py -f “/path/to/file” ‑‑profile <profile> psxview



Output differences:
- Volatility 2: Additional process lists with psxview
- Volatility 3: Does not include a direct psxview equivalent



PROCDUMP

Volatility 2
Volatility 3

vol.py -f “/path/to/file” ‑‑profile <profile> procdump -p <PID> ‑‑dump-dir=“/path/to/dir”



Output differences:
- Volatility 2: Just outputs specified PID (or all if not specified)
- Volatility 3: Dumps exe and associated DLLs



MEMDUMP

Volatility 2
Volatility 3

vol.py -f “/path/to/file” ‑‑profile <profile> memdump -p <PID> ‑‑dump-dir=“/path/to/dir”



HANDLES

Volatility 2
Volatility 3

vol.py -f “/path/to/file” windows.handles ‑‑pid <PID>



Output differences:
- Volatility 2: Offset(V), PID, handle, access, type, details
- Volatility 3: PID, process, offset, handlevalue, type, grantedaccess, name



DLLS

Volatility 2
Volatility 3

vol.py -f “/path/to/file” windows.dlllist ‑‑pid <PID>



Output differences:
- Volatility 2: PID, command line, base, size, loadcount, loadtime, path
- Volatility 3: PID, process, base, size, name, path, loadtime, file output



CMDLINE

Volatility 2
Volatility 3

vol.py -f “/path/to/file” windows.cmdline

Output differences:
- Volatility 2: process name, PID, commandline; cmdscan includes application, flags, process handle; consoles contains C:\ listing, original titles, screen position and command history information
- Volatility 3: PID, process name, args




NETWORK INFORMATION
NETSCAN

Volatility 2
Volatility 3

vol.py -f “/path/to/file” windows.netscan

vol.py -f “/path/to/file” windows.netstat



Note: The XP/2003 specific plugins are deprecated and therefore not available in Volatility 3




REGISTRY
HIVELIST

Volatility 2
Volatility 3

vol.py -f “/path/to/file” windows.registry.hivescan

vol.py -f “/path/to/file” windows.registry.hivelist



PRINTKEY

Volatility 2
Volatility 3

vol.py -f “/path/to/file” windows.registry.printkey

vol.py -f “/path/to/file” windows.registry.printkey ‑‑key “Software\Microsoft\Windows\CurrentVersion”



HIVEDUMP

Volatility 2
Volatility 3

vol.py -f “/path/to/file” ‑‑profile <profile> printkey




FILES
FILESCAN

Volatility 2
Volatility 3

vol.py -f “/path/to/file” windows.filescan



FILEDUMP

Volatility 2
Volatility 3

vol.py -f “/path/to/file” -o “/path/to/dir” windows.dumpfiles

vol.py -f “/path/to/file” -o “/path/to/dir” windows.dumpfiles ‑‑virtaddr <offset>

vol.py -f “/path/to/file” -o “/path/to/dir” windows.dumpfiles ‑‑physaddr <offset>




MISCELLANEOUS
MALFIND

Volatility 2
Volatility 3

vol.py -f “/path/to/file” windows.malfind



Output differences:
- Volatility 2: PID, process name, address, VAD tags, hexdump, and shellcode
- Volatility 3: PID, process name, process start, protection, commit charge, privatememory, file output, hexdump disassembly



YARASCAN

Volatility 2
Volatility 3

vol.py -f “/path/to/file” windows.vadyarascan ‑‑yara-rules <string>

vol.py -f “/path/to/file” windows.vadyarascan ‑‑yara-file “/path/to/file.yar”

vol.py -f “/path/to/file” yarascan.yarascan ‑‑yara-file “/path/to/file.yar”
