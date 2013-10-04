aws
===

If you're like me, you find looking up IP/key combos in order to SSH into Linux EC2 hosts pretty annoying.  Managing multiple AWS accounts takes this to another level.  'aws' (it might expand beyond EC2) seeks to mitigate this, with a few assumptions that will hopefully be self-explanatory after a 'git clone':

1. you have an ~/aws/ directory
2. you have an ~/aws/accounts/ directory with account data
3. you have an ~/aws/keys/ directory with SSH keys
4. you have an ~/aws/ec2-api-tools/ directory with [the EC2 API tools](http://aws.amazon.com/developertools/351)

Edit account(s), add key(s), and fetch the EC2 API tools.  I recommend aliasing '~/aws/bin/aws'.

Note: 'aws' currently operates on **running** instances with IP addresses.

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

Running a command on all instances for a given account (this works for all accounts too) (danger!):
```bash
# aws example2 uname -m
example2/example2-db01: x86_64
example2/example2-db02: x86_64
```

BONUS: source the script and it will set up an API account tool usage env in your current shell
```bash
# . ~/aws/bin/aws example1
# ec2-describe-instances
```
