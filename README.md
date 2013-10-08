aws
===

I find looking up IP/key combos in order to SSH into Linux EC2 hosts pretty annoying.  Managing multiple AWS accounts takes this to another level.  'aws' (it might expand beyond EC2) seeks to mitigate this.  Clone it into your home directory, add your accounts and SSH keys, and fetch [the EC2 API tools](http://aws.amazon.com/developertools/351).

Usage and account list:
```bash
# aws
usage: /Users/astrostl/aws/bin/aws [account|all] [command]
example1 example2
```

Displaying "account/nametag: ssh string" for a given account:
```bash
# aws example1
example1/example1-web01: ssh -i ~/aws/keys/example1.pem ec2-user@ec2-1-2-3-4.compute-1.amazonaws.com
example1/example1-web02: ssh -i ~/aws/keys/example1.pem ec2-user@ec2-2-3-4-5.compute-1.amazonaws.com
```

Displaying "account/nametag: ssh string" for ALL accounts:
```bash
# aws all
example1/example1-web01: ssh -i ~/aws/keys/example1.pem ec2-user@ec2-1-2-3-4.compute-1.amazonaws.com
example1/example1-web02: ssh -i ~/aws/keys/example1.pem ec2-user@ec2-2-3-4-5.compute-1.amazonaws.com
example2/example2-db01: ssh -i ~/aws/keys/example2.pem ec2-user@ec2-3-4-5-6.compute-1.amazonaws.com
example2/example2-db02: ssh -i ~/aws/keys/example2.pem ec2-user@ec2-4-5-6-7.compute-1.amazonaws.com
```

Running a command on all instances for a given account (danger!) (this works for the "all" target too):
```bash
# aws example2 uname -m
example2/example2-db01: x86_64
example2/example2-db02: x86_64
```

Running a command on a specific instance in a given account (danger!):
```bash
# aws example2/example2-db01 uname -m
example2/example2-db01: x86_64
```

INTERACTIVE login to a specific instance in a given account:
```bash
# aws example2/example2-db01 -i
[ec2-user@domU-00-11-22-33-44-55 ~]$
```

BONUS: source the script and it will set up a direct API account tool usage env in your current shell
```bash
# . ~/aws/bin/aws example1
# ec2-describe-instances
```
