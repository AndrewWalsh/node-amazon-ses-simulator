# node-amazon-ses-simulator

[![npm version](https://badge.fury.io/js/node-amazon-ses-simulator.svg)](https://badge.fury.io/js/node-amazon-ses-simulator)

A local server that simulates responses from Amazon's Simple Email Service (SES).

[![Screen Shot 2017-02-01 at 03.54.47.png](https://s29.postimg.org/4j0uh0xvb/Screen_Shot_2017_02_01_at_03_54_47.png)](https://postimg.org/image/hzxszw86r/)

## Getting Started

Install locally and run with:

```
npm install -D node-amazon-ses-simulator
node ./node_modules/node-amazon-ses-simulator/index.js --help
```
Otherwise, install globally:

```
npm install -g node-amazon-ses-simulator
node-amazon-ses-simulator --help
```

Your server's AWS.SES config will need to point towards the right endpoint:

```
const ses = new AWS.SES({
    accessKeyId,
    secretAccessKey,
    secretKey,
    region,
    endpoint: 'http://localhost:9999' // See this line
  });
```

## What and why

Put simply - the server will respond with valid XML that Amazon's SDK will accept.

Amazon have their own [test server](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/mailbox-simulator.html) but it isn't free - with the same cost as regular emails. This can be frustrating when you need to test services sending large volumes of emails.

## Command line args

This module accepts several arguments. All are optional.


| Name            | Type                    | Description                                                 | Default             |
|-----------------|-------------------------|-------------------------------------------------------------|---------------------|
| -h --host       | string                  | Set the hostname                                            | localhost           |
| -p --port       | number                  | Set the port                                                | 9999                |
| -i --interval   | number                  | Interval between req reports (ms)                           | 1000                |
| -v --validate   | boolean                 | Should validate emails                                      | false               |
| -e --error      | number                  | Percentage chance of throttling error                       | 0                   |
