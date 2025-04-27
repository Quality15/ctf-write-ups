# packer
Write-Up by **Mttttt** *2024-05-29*

## Task description
Reverse this linux executable? [binary](https://artifacts.picoctf.net/c_titan/20/out)

- *Category*: **Reverse Engineering**
- *Difficulty*: **Meduim**

## Solution
Download the file and find out that this executable was packed with UPX

Decompile it with UPX:
```bash
upx -d out
```

### Solution 1
Then, look at the strings of file by following command:
```bash
strings out | less
```

And search for word flag

Get this result
`7069636f4354467b5539585f556e5034636b314e365f42316e34526933535f62646438343839337d`

Put in in the CyberChef and decode with HEX

Result is out flag

### Solution 2
Send file to Ghidra and analyse it

After Ghidra finish analyzing our file, lets review pseudo-code of `main` function

```C
undefined8 main(void)

{
  size_t sVar1;
  char *pcVar2;
  int iVar3;
  undefined *puVar4;
  long in_FS_OFFSET;
  undefined auStack_a8 [8];
  size_t local_a0;
  undefined8 local_98;
  char *local_90;
  undefined8 local_88;
  undefined8 local_80;
  undefined8 local_78;
  undefined8 local_70;
  undefined8 local_68;
  undefined8 local_60;
  undefined8 local_58;
  undefined8 local_50;
  undefined8 local_48;
  undefined8 local_40;
  undefined8 local_38;
  undefined8 local_30;
  undefined4 local_28;
  long local_20;
  
  local_20 = *(long *)(in_FS_OFFSET + 0x28);
  local_a0 = 100;
  local_98 = 99;
  for (puVar4 = auStack_a8; puVar4 != auStack_a8; puVar4 = puVar4 + -0x1000) {
    *(undefined8 *)(puVar4 + -8) = *(undefined8 *)(puVar4 + -8);
  }
  *(undefined8 *)(puVar4 + -8) = *(undefined8 *)(puVar4 + -8);
  local_88 = 0x6636333639363037;
  local_80 = 0x6237363434353334;
  local_78 = 0x6635383539333535;
  local_70 = 0x3433303565363535;
  local_68 = 0x6534313362363336;
  local_60 = 0x3133323466353633;
  local_58 = 0x3936323534336536;
  local_50 = 0x3236663533353333;
  local_48 = 0x3433383334363436;
  local_40 = 0x6437333339333833;
  local_38 = 0;
  local_30 = 0;
  local_28 = 0;
  local_90 = puVar4 + -0x70;
  *(undefined8 *)(puVar4 + -0x78) = 0x401eee;
  printf("Enter the password to unlock this file: ");
  pcVar2 = local_90;
  sVar1 = local_a0;
  *(undefined8 *)(puVar4 + -0x78) = 0x401f0f;
  fgets(pcVar2,(int)sVar1,(FILE *)stdin);
  pcVar2 = local_90;
  *(undefined8 *)(puVar4 + -0x78) = 0x401f2a;
  printf("You entered: %s\n",pcVar2);
  pcVar2 = local_90;
  sVar1 = local_a0;
  *(undefined8 *)(puVar4 + -0x78) = 0x401f47;
  iVar3 = strncmp(pcVar2,(char *)&local_88,sVar1);
  if (iVar3 == 0) {
    *(undefined8 *)(puVar4 + -0x78) = 0x401f57;
    puts(
        "Password correct, please see flag: 7069636f4354467b5539585f556e5034636b314e365f42316e345269 33535f62646438343839337d"
        );
    *(undefined8 *)(puVar4 + -0x78) = 0x401f63;
    puts((char *)&local_88);
  }
  else {
    *(undefined8 *)(puVar4 + -0x78) = 0x401f71;
    puts("Access denied");
  }
  if (local_20 == *(long *)(in_FS_OFFSET + 0x28)) {
    return 0;
  }
                    /* WARNING: Subroutine does not return */
  __stack_chk_fail();
}

```

In this code we can find our encoded flag
`"Password correct, please see flag: 7069636f4354467b5539585f556e5034636b314e365f42316e345269 33535f62646438343839337d"`

Decode it from HEX and result will be out final flag

## Answer
`picoCTF{U9X_UnP4ck1N6_B1n4Ri3S_bdd84893}`
