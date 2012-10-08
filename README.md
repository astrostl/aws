aws
===

I happen to manage a bunch of EC2 hosts from a bunch of individual AWS accounts. I find it terribly annoying to log into individual AWS consoles in order to
 determine which IP/key combo I should use to log into a given instance.

'aws/bin/aws' (named so because I might expand it to do more than just EC2)
 addresses this, and makes several assumptions:

1. you have a root ~/aws/ directory
2. you have an ~/aws/accounts/ directory with account data
3. you have an ~/aws/keys/ directory with SSH keys
4. you have an ~/aws/ec2-api-tools/ directory with the EC2 API tools

The example layout here reflects that.  The 'aws' script itself can technically
 live anywhere, but I recommend pathing it.

```bash
# aws
usage: /Users/astrostl/aws/bin/aws [account]
example1	example2
```

```bash
# aws example1
example1-web01: ssh -i ~/aws/keys/example1.pem ec2-user@ec2-1-2-3-4.compute-1.amazonaws.com
example1-web02: ssh -i ~/aws/keys/example1.pem ec2-user@ec2-2-3-4-5.compute-1.amazonaws.com
```

```bash
# aws example2
example2-db01: ssh -i ~/aws/keys/example2.pem ec2-user@ec2-3-4-5-6.compute-1.amazonaws.com
example2-db02: ssh -i ~/aws/keys/example2.pem ec2-user@ec2-4-5-6-7.compute-1.amazonaws.com
```
