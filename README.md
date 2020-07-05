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
   - Satisfy the [minimum requirements](https://ghidra-sre.org/InstallationGuide.html#Requirements) (Java 11 JDK) and download Ghidra from the above website.
   - After extracting the downloaded Ghidra package, open `ghidraRun.bat` to start.
   - Select New project > Import Files, then select your binary file to analyze.
   - In the `Symbol Tree` tab on the left, find and select `main` under `Functions`.
   - Then, select `Windows` > `Decompile:main` from the top menu to see readable code.
4. [StegSolve](https://github.com/zardus/ctf-tools/blob/master/stegsolve/install): A java app that solves steganography by apply various filters.
   - Installation instruction is in the above link.
5. [Burp Suite Professional](https://portswigger.net/burp/pro): A software that can use proxy (usually localhost:8080) to intercept HTTP requests. You can edit and resend the requests.
   - The Community version is very slow.. don't use it. You should be able to find free professional licenses online:)
6. [IDA Pro 32/64 bit](https://www.hex-rays.com/products/ida/support/download_freeware/):
   - Download IDA Pro 64-bit from the above link, and download IDA Pro 32-bit with pseudocode decompiler [here](https://drive.google.com/open?id=1CCRnlhXZCUwH1P5WisLf6CQtHv6dTtFZ).
   - Hotkeys:
     - `F5`: view pseudocode
     - `tab`: toggle between the disassembly code view and pseudocode view.
     - `Shift+F12`: view all strings in the program.
   - Note that 32-bit programs need to be opened with IDA Pro 32-bit, and vice versa.
   - Reference: [IDA Pro Hotkey Cheatsheet](https://www.hex-rays.com/products/ida/support/freefiles/IDA_Pro_Shortcuts.pdf)

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
3. **`kill $(lsof -t -i:8080)`: Kill any process listening on port 8080.**
   - reference: [StackOverflow](https://stackoverflow.com/questions/11583562/how-to-kill-a-process-running-on-particular-port-in-linux)
4. **`display <image_name>`: Display image from terminal.**
   - Make sure that [imagemagick](https://tecadmin.net/install-imagemagick-on-linux/) is installed before using this.
   - reference: [StackExchange](https://unix.stackexchange.com/questions/35333/what-is-the-fastest-way-to-view-images-from-the-terminal)
5. **`nc -l -p 9000`: Listen on port 9000**
   - use `nc <ip_address> 9000` to communicate with the host.
6. **`grep -rnw '/path/to/somewhere/' -e 'pattern'`: Find all files containing the pattern under the specified path.**
   - `-r`: recursively search
   - `-n`: display the line number containing the pattern in the file.
   - `-w`: match the entire word of the pattern.
   - Reference: [StackOverflow](https://stackoverflow.com/questions/16956810/how-do-i-find-all-files-containing-specific-text-on-linux)
7. **`strings <filename>`: Print all strings in the file.**
   - use `strings <filename> | grep -E <some_regex>` to find the strings that matches the regular expression, `FLAG{[a-zA-Z0-9_!@]+}`, for example.
   - Test regular expressions online at https://regexr.com/.
8. **`strace <filename>`: Print out system call details.**
   - If not installed, run `sudo apt-get install strace`.
   - Use `strace -s 50 <filename>` to print out the strings with max length 50.
   - Reference: [manual](https://man7.org/linux/man-pages/man1/strace.1.html)
9. **`objdump -M intel -d <filename> | less`: Show the disassembled file.**
   - `-M intel`: display the assembly in Intel syntax (see the differences between the default AT&T syntax and the Intel syntax in [wiki](https://en.wikipedia.org/wiki/X86_assembly_language#Syntax)).
   - `-d`: disassemble
   - The `less` command is for viewing the contents of the file, allow both forward and backward navigation. (The `more` command only allow forward navigation.)
   - When using `less` to view the file, you can use `/<anything_you_want_to_search>` to search for specific strings. For example, use `/main` to locate the main function.
   - Reference: [manual](https://sourceware.org/binutils/docs/binutils/objdump.html)

## :sun_with_face: Learning / Practicing Websites

1. **[PortSwigger](https://portswigger.net/web-security/all-labs)**: Its web security lab covers topics across SQL injection, Cross-site scripting, Cross-site request forgery (CSRF), Cross-origin resource sharing (CORS), Server-side request forgery (SSRF), etc.
2. **[OWASP Juice Shop](https://owasp.org/www-project-juice-shop/)**: An insecure web application for you to attack! ([reference solutions](https://bkimminich.gitbooks.io/pwning-owasp-juice-shop/content/appendix/solutions.html))

## :sun_with_face: Special Thanks

- Cute emojis from [here](https://gist.github.com/rxaviers/7360908)! :blush:
