aws
===

I manage a bunch of individual AWS accounts, and find it terribly annoying to look up IP/key combos using individual AWS consoles.  'aws' (it might expand beyond EC2) addresses this, with several assumptions:

1. you have an ~/aws/ directory
2. you have an ~/aws/accounts/ directory with account data
3. you have an ~/aws/keys/ directory with SSH keys
4. you have an ~/aws/ec2-api-tools/ directory with [the EC2 API tools](http://aws.amazon.com/developertools/351)

Check this out into your home dir, grab the EC2 API tools, edit, and you're set.  I recommend pathing/aliasing 'bin/aws'.

```bash
# aws
usage: /Users/astrostl/aws/bin/aws [account|all] [command]
example1 example2
```

```bash
# aws example1
example1/example1-web01: ssh -i ~/aws/keys/example1.pem ec2-user@ec2-1-2-3-4.compute-1.amazonaws.com
example1/example1-web02: ssh -i ~/aws/keys/example1.pem ec2-user@ec2-2-3-4-5.compute-1.amazonaws.com
```

```bash
# aws all
example1/example1-web01: ssh -i ~/aws/keys/example1.pem ec2-user@ec2-1-2-3-4.compute-1.amazonaws.com
example1/example1-web02: ssh -i ~/aws/keys/example1.pem ec2-user@ec2-2-3-4-5.compute-1.amazonaws.com
example2/example2-db01: ssh -i ~/aws/keys/example2.pem ec2-user@ec2-3-4-5-6.compute-1.amazonaws.com
example2/example2-db02: ssh -i ~/aws/keys/example2.pem ec2-user@ec2-4-5-6-7.compute-1.amazonaws.com
```

```bash
# aws example2 uname -a
example2/example2-db01: Linux
example2/example2-db02: Linux
```

BONUS: source the script in order to use any account-targeted EC2 API tools
```bash
# . ~/aws/bin/aws example1
# ec2-describe-instances
```
