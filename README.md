# Welcome to your CDK TypeScript project

This is a blank project for CDK development with TypeScript.

The `cdk.json` file tells the CDK Toolkit how to execute your app.

## Useful commands

* `npm run build`   compile typescript to js
* `npm run watch`   watch for changes and compile
* `npm run test`    perform the jest unit tests
* `cdk deploy`      deploy this stack to your default AWS account/region
* `cdk diff`        compare deployed stack with current state
* `cdk synth`       emits the synthesized CloudFormation template

npm install mersenne-twister
npm install --save @types/mersenne-twister

# create s3 bucket
# setup role for s3 bucket putobject
### fluent-bit
# install fluent-bit
curl https://raw.githubusercontent.com/fluent/fluent-bit/master/install.sh | sh


# forwarder 
### td agent
# install td-agent fluentd
curl -L https://toolbelt.treasuredata.com/sh/install-amazon2-td-agent3.sh | sh

# setup /etc/init.d/td-agent 
 td-agent to root
# setup  /usr/lib/systemd/system/td-agent.service
 td-agent to root
# setup /etc/td-agent/td-agent.conf

# forwarder instance
<source>
  @type syslog
  port 514
  bind 0.0.0.0
  @id input_forward
  tag td.messages.forwarded
</source>
<match td.messages.syslog.*>
  @type s3
  s3_bucket __BUCKET_NAME__
  s3_region ap-northeast-1
  time_slice_format %Y%m%d%H%M
  <buffer>
    @type "file"
    path "/var/log/td-agent/buffer/s3/"
    timekey 1200
    timekey_wait 10m
    chunk_limit_size 2m
  </buffer>
</match>

# sender
# /etc/rsyslog.conf
*.* @__FORWARDER_PORT__:__SYSLOG_PORT__
