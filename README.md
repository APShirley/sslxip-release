# SSLIP Release

SSLIP is a [BOSH release](https://bosh.io/docs/create-release.html)
of a [PowerDNS](https://www.powerdns.com/) nameserver combined with
a modified [xip.io](http://xip.io/) pipe backend.

## Deploying to Amazon AWS

Clone the git repository and create the BOSH release:

```
git clone https://github.com/APShirley/sslxip-release.git
cd sslxip-release
 # download the PowerDNS source
curl -L https://downloads.powerdns.com/releases/pdns-3.4.5.tar.bz2 -o src/powerdns/pdns-3.4.5.tar.bz2
bosh create release --force --with-tarball
```

Copy the sample configuration in examples/sslip-aws.yml and customize
entries flagged with **CHANGEME**. You will need an Amazon AWS account with a configured VPC.

```
cp examples/sslip-aws.yml /tmp/
vim /tmp/sslip-aws.yml
```

Deploy the release to AWS.

```
bosh-init deploy /tmp/sslip-aws.yml
```
