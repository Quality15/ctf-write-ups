# Verify
Write-Up by **Mttttt** *2024-05-29*

## Task description
People keep trying to trick my players with imitation flags. I want to make sure they get the real thing! I'm going to provide the SHA-256 hash and a decrypt script to help you know that my flags are legitimate. You can download the challenge files here:

- `[challenge.zip](https://artifacts.picoctf.net/c_rhea/20/challenge.zip)`

- *Category*: **Forensics**
- *Difficulty*: **Easy**

## Solution
I tried with downloading file `challanged.zip` but final solultion wasn't correct

Alright, connect to ssh

See content of file `chechsum.txt`

See `decrypt.sh` code
To use this script we need to provide it a file with correct checksum (it is in file `checksum.txt`)

We can get checksum of file with this command:
```bash
sha256sum <file>
```

To see all checksums of files in directory `files/` use this command:
```bash
sha256sum files/*
```

To see only file that we need use this command:

```bash
sha256sum files/* | grep fba9f49bf22aa7188a155768ab0dfdc1f9b86c47976cd0f7c9003af2e20598f7
```
Output:
`fba9f49bf22aa7188a155768ab0dfdc1f9b86c47976cd0f7c9003af2e20598f7   files/87590c24`

Then use script with this file:
```bash
./decrypt.sh files/87590c24
```

## Answer
`picoCTF{trust_but_verify_87590c24}`
