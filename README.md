# :sun_with_face: Awesome Security Tool List & Useful Commands :four_leaf_clover:

This is a list of security tools & commands that I have used or recommend. I'm using Kali Linux. Welcome any contributions! :muscle:

& Wish you all good luck on your way of finding the hidden treasures. :wink:

## :sun_with_face: Tools

1. [Binwalk](https://github.com/ReFirmLabs/binwalk): Firmware analysis & reverse engineering.
   - **Example: `binwalk -Mre <filename>`**
   - `-M`: recursively scan extracted files.
   - `-r`: delete carved file after extraction. ([what is file carving?](https://resources.infosecinstitute.com/file-carving/#gref))
   - `-e`: extract known file types.
2. [qemu-mipsel](https://www.qemu.org/docs/master/system/target-mips.html): Execute MIPS programs on non-MIPS OS.

   - **Example: `qemu-mipsel <filename>`**
   - If you run into "No such file or directory", run `export QEMU_LD_PREFIX=<folder_location_of_the_missing_file>` and retry the above command to help the program find your file.
   - QEMU: Quick EMUlator
   - mipsel: little-endian MIPS / mips: big-endian MIPS ([little vs big endian?](https://chortle.ccsu.edu/AssemblyTutorial/Chapter-15/ass15_3.html))

3. [Ghidra](https://ghidra-sre.org/): Decompile binary files.
   - Satisfy the [minimum requirements](https://ghidra-sre.org/InstallationGuide.html#Requirements) (Java 11 JDK) and then download Ghidra from the above website.
   - After extracting the downloaded Ghidra package, open `ghidraRun.bat` to start.
   - Select New project > Import Files, then select your binary file to analyze.
   - In the `Symbol Tree` tab on the left, find and select `main` under `Functions`.
   - Then, select `Windows` > `Decompile:main` from the top menu to see readable code.

## :sun_with_face: Common Commands

1. **`lsof -i -P -n | grep LISTEN`: Show listening ports.**
   - lsof: list open files and processes that opened them.
   - `-i`: list all network connections.
   - `-P`: list port number instead of port name.
   - `-n`: don't convert network number to hostname, this can make lsof run faster.
   - reference: [manual](https://man7.org/linux/man-pages/man8/lsof.8.html)
2. **`xdg-open .`: Open current folder in GUI explorer.**
   - This is useful for drag and drop files from Linux VM to host computer.
   - reference: [StackExchange](https://askubuntu.com/questions/31069/how-to-open-a-file-manager-of-the-current-directory-in-the-terminal)
3.

## :sun_with_face: Special Thanks

- Cute emojis from [here](https://gist.github.com/rxaviers/7360908)! :blush:
