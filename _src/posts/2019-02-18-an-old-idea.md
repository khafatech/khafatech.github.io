    Title: An old IDEA
    Date: 2019-02-18T17:33:20
    Tags: security, encryption


Spoiler alert: I didn't find the password.


Around 2002, I came across a tool that encrypts and decrypts files using the IDEA cipher. [IDEA](https://en.wikipedia.org/wiki/International_Data_Encryption_Algorithm) was created in 1991 by James Massey Xuejia Lai, and it seems still relatively secure. It's still used in a recent version of opengpg.


I had encrypted few zip files using this, in 2002 and 2003. (Nothing serious, just wanted to try out encrypting things.) However, I forgot the passwords.

Looking at the implementation, it says it uses a maximum of 8 characters for a passphrase, which is about half of IDEA's 128-bit keylength (not counting non-ascii characters.) 

It was a tool for DOS in 16-bit mode. 

Given this limitation, is bruteforcing a password possible? If I used only lowercase letters for the password, the number of passwords to try would be `26^8 = 208,827,064,576`, or about 200 billion combinations. Alphanumeric combinations would be `(26*2 + 10)^8 = 218,340,105,584,896`, or about 218 trillion. Some simple math can lead us to an estimate of the time to go through the search space. It depends on the elements and elements/s.


One challenge with finding the correct decryption password is there's no easy way of making sure we hae the correct password. The way this idea program worked was to only encrypt/decrypt fixed blocks, with no integrity checking. If we decrypt a file with the wrong password, it would output random data. So one way to find the correct password is to find a pattern in the output if we know what the output would contain. Since it was a zip file, a zip file has a known header in the first block (16 bytes).


I modified the main file to read words from a wordlist, decrypt the first block, and test if it's a zip header. Instead of parallizing the solution in C, I wrote simple bash scripts to run it parallelly after splitting the wordlist into 4, the number of cores I have. I was able to process 700k passwords/s. I wasn't able to find the password using the wordlists I had. I suppose I need to investigate more techniques and maybe harness my GPU.


Few more things come to my mind for future work:

- Are there any other weaknesses in the implementation?
- Could this be integrated into the "John the Ripper" password cracker?



### References

* [The IDEA code that compiles in a modern linux enviornment](https://github.com/quakehead/idea)

* [The IDEA algorithm](https://en.wikipedia.org/wiki/International_Data_Encryption_Algorithm)
