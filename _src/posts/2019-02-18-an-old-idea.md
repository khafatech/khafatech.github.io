    Title: An old IDEA
    Date: 2019-02-18T17:33:20
    Tags: security, encryption


Around 2002, I came across a tool that encrypts and decrypts files using the IDEA cipher. [IDEA](https://en.wikipedia.org/wiki/International_Data_Encryption_Algorithm) was created in 1991 by James Massey Xuejia Lai, and it seems still relatively secure. It's still used in a recent version of opengpg.



I had encrypted few zip files using this, in 2002 and 2003. (Nothing seriuos, just wanted to try out encrypting things.) However, I forgot the passwords.

Looking at the implementation, it says it uses a maximum of 8 characters for a passphrase, which is about half of IDEA's 128-bit keylength (not counting non-ascii characters.) 

It was a tool for DOS in 16-bit mode.

So given this limitation, is bruteforcing a password possible? If I used only lowercase letters for the password, the number of passwords to try would be `26^8 = 208,827,064,576`, or about 200 billion combinations. Alphanumeric combinations would be `(26*2 + 10)^8 = 218,340,105,584,896`, or about 218 trillion.



Few things come to my mind:

- Are there any other weaknesses in the implementation?
- thing2
- thing3


