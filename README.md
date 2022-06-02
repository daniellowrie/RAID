# RAID
[R]emove [A]mazon [ID]entification
==================================

When demoing anything with AWS through the awscli, sensitive info might leak out.
These are things like AccountID and RoleID.

This script will obfuscate/remove those pieces from the output of the awscli.

RAID will also accept and run obfuscated input.

To run, either run from your current directory, add RAID script directory to $PATH, or move RAID script to path in $PATH.

Don't forget to 
```chmod +x raid``` and to change the ```AWS_Account_ID``` variable to YOUR AWS ACCOUNT ID

then add 'raid' to the front of your awscli commands.

so this:

  ```
  dlowrie@localhost:~$ aws --profile cloudguy sts get-caller-identity
  ```

becomes:
  ```
  dlowrie@localhost:~$ raid aws --profile cloudguy sts get-caller-identity
  {
    "UserId": "AIDA6ILMW2DNTDVZQMAYY",
    "Account": "XXXXXXXXXXXX",
    "Arn": "arn:aws:iam::XXXXXXXXXXXX:user/cloudguy"
  }
  ```
