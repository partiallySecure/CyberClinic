# Password Cracking Tools

## Hashcat

Hashcat is a popular open-source software for cracking passwords that can crack various hashes using various attack modes. 

### Dictionary Attack

```markdown
hashcat -m <hash_mode> -a 0 -o cracked.txt hashes.txt wordlist.txt
```

- Replace `<hash_mode>` with the appropriate hash mode identifier (e.g., 0 for MD5, 1000 for NTLM).
- Replace `hashes.txt` with the file containing the password hashes you want to crack.
- Replace `wordlist.txt`  with the wordlist file you wish to use
- `-a 0`  is a Dictionary Attack mode which will be performed with a wordlist
- `-o`  indicates the output file, in this case it is ‘cracked.txt’

To identify the correct `<hash_mode>` , match the format of the hash to those in the list on the example hashes webpage:

[https://hashcat.net/wiki/doku.php?id=example_hashes](https://hashcat.net/wiki/doku.php?id=example_hashes)

### Mask Attack

The mask attack is similar to the dictionary attack, but it is more specific. Brute-force approaches like dictionary attacks can take a long time to crack a password. But if we have information regarding the password, we can use that to speed up the time it takes to crack the password.

Hashcat has built-in charsets that can be combined to create a custom mask:

```prolog
?l = abcdefghijklmnopqrstuvwxyz
?u = ABCDEFGHIJKLMNOPQRSTUVWXYZ
?d = 0123456789
?h = 0123456789abcdef
?H = 0123456789ABCDEF
?s = «space»!"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
?a = ?l?u?d?s
?b = 0x00 - 0xff
```

Example: cracking hash for password starting “susan_nasus_” followed by a random number between 1-1,000,000,000

```jsx
hashcat -m 1400 hash.txt -a 3 susan_nasus_?d?d?d?d?d?d?d?d?d
```

More information on mask attacks:

[https://hashcat.net/wiki/doku.php?id=mask_attack](https://hashcat.net/wiki/doku.php?id=mask_attack)

## Hydra

Hydra is an open-source, password brute-forcing tool which can be used in various online brute-forcing attacks, such as for SSH, RDP, HTTP basic authentication and as well as on HTML forms.

### SSH Brute-Force Using Wordlist

In this example, the `-l` indicates the username being used, alternatively if you wish to use a list of usernames, `-L` can be used instead. 

`-P`  specifies the password list being used in the attack.

`-t`  is set to 4, which sets the number of parallel tasks (threads) to run.

```prolog
hydra -l msfadmin -P rockyou.txt 192.168.29.69 ssh -t 4
```

### HTTP Basic Authentication Brute-Force

This example demonstrates how to conduct a brute-force attack against a web server using HTTP basic authentication:

```prolog
hydra -l admin -P rockyou.txt localhost http-get
```

## John The Ripper

John The Ripper is like Hashcat in that it is useful for offline attacks/ cracking hashes. 

### Dictionary Mode

Uses a wordlist to generate hashes and compare them with the password hash.

In this example, ‘crack.txt’ indicates a text file with the password hash in it:

```prolog
john --wordlist=rockyou.txt --format=raw-sha1 crack.txt
```

### Incremental Mode

This mode is the most powerful mode in John, where it tries all possible character combinations as passwords. This mode is a last resort if all wordlists and other attacks fail (it takes a really long time).

In this example, the `-i`  flag indicates the use of increment mode, the `digits`  placeholder can be used to set the maximum number of digits in the password:

```prolog
john -i:digits passwordfile.txt
```