---
title: "Transport Options"
isDefaultIndex: false
generated: true
---
<!-- This file was generated from the Vendure source. Do not modify. Instead, re-run the "docs:build" script -->
import MemberInfo from '@site/src/components/MemberInfo';
import GenerationInfo from '@site/src/components/GenerationInfo';
import MemberDescription from '@site/src/components/MemberDescription';


## EmailTransportOptions

<<<<<<< HEAD
<GenerationInfo sourceFile="packages/email-plugin/src/types.ts" sourceLine="132" packageName="@bb-vendure/email-plugin" />
=======
<GenerationInfo sourceFile="packages/email-plugin/src/types.ts" sourceLine="171" packageName="@vendure/email-plugin" />
>>>>>>> upstream/master

A union of all the possible transport options for sending emails.

```ts title="Signature"
type EmailTransportOptions = | SMTPTransportOptions
    | SendmailTransportOptions
    | FileTransportOptions
    | NoopTransportOptions
    | SESTransportOptions
    | TestingTransportOptions
```


## SMTPTransportOptions

<<<<<<< HEAD
<GenerationInfo sourceFile="packages/email-plugin/src/types.ts" sourceLine="147" packageName="@bb-vendure/email-plugin" />
=======
<GenerationInfo sourceFile="packages/email-plugin/src/types.ts" sourceLine="186" packageName="@vendure/email-plugin" />
>>>>>>> upstream/master

The SMTP transport options of [Nodemailer](https://nodemailer.com/smtp/)

```ts title="Signature"
interface SMTPTransportOptions extends SMTPTransport.Options {
    type: 'smtp';
    logging?: boolean;
}
```
* Extends: <code>SMTPTransport.Options</code>



<div className="members-wrapper">

### type

<MemberInfo kind="property" type={`'smtp'`}   />


### logging

<MemberInfo kind="property" type={`boolean`} default={`false`}   />

If true, uses the configured <a href='/reference/typescript-api/logger/vendure-logger#vendurelogger'>VendureLogger</a> to log messages from Nodemailer as it interacts with
the SMTP server.


</div>


## SESTransportOptions

<<<<<<< HEAD
<GenerationInfo sourceFile="packages/email-plugin/src/types.ts" sourceLine="196" packageName="@bb-vendure/email-plugin" />
=======
<GenerationInfo sourceFile="packages/email-plugin/src/types.ts" sourceLine="235" packageName="@vendure/email-plugin" />
>>>>>>> upstream/master

The SES transport options of [Nodemailer](https://nodemailer.com/transports/ses//)

See [Nodemailers's SES docs](https://nodemailer.com/transports/ses/) for more details

*Example*

```ts
 import { SES, SendRawEmailCommand } from '@aws-sdk/client-ses'

 const ses = new SES({
    apiVersion: '2010-12-01',
    region: 'eu-central-1',
    credentials: {
        accessKeyId: process.env.SES_ACCESS_KEY || '',
        secretAccessKey: process.env.SES_SECRET_KEY || '',
    },
 })

 const config: VendureConfig = {
  // Add an instance of the plugin to the plugins array
  plugins: [
    EmailPlugin.init({
      handler: defaultEmailHandlers,
      templatePath: path.join(__dirname, 'static/email/templates'),
      transport: {
        type: 'ses',
        SES: { ses, aws: { SendRawEmailCommand } },
        sendingRate: 10, // optional messages per second sending rate
      },
    }),
  ],
};
 ```

```ts title="Signature"
interface SESTransportOptions extends SESTransport.Options {
    type: 'ses';
}
```
* Extends: <code>SESTransport.Options</code>



<div className="members-wrapper">

### type

<MemberInfo kind="property" type={`'ses'`}   />




</div>


## SendmailTransportOptions

<<<<<<< HEAD
<GenerationInfo sourceFile="packages/email-plugin/src/types.ts" sourceLine="207" packageName="@bb-vendure/email-plugin" />
=======
<GenerationInfo sourceFile="packages/email-plugin/src/types.ts" sourceLine="246" packageName="@vendure/email-plugin" />
>>>>>>> upstream/master

Uses the local Sendmail program to send the email.

```ts title="Signature"
interface SendmailTransportOptions {
    type: 'sendmail';
    path?: string;
    newline?: string;
}
```

<div className="members-wrapper">

### type

<MemberInfo kind="property" type={`'sendmail'`}   />


### path

<MemberInfo kind="property" type={`string`}   />


### newline

<MemberInfo kind="property" type={`string`}   />




</div>


## FileTransportOptions

<<<<<<< HEAD
<GenerationInfo sourceFile="packages/email-plugin/src/types.ts" sourceLine="222" packageName="@bb-vendure/email-plugin" />
=======
<GenerationInfo sourceFile="packages/email-plugin/src/types.ts" sourceLine="261" packageName="@vendure/email-plugin" />
>>>>>>> upstream/master

Outputs the email as an HTML file for development purposes.

```ts title="Signature"
interface FileTransportOptions {
    type: 'file';
    outputPath: string;
    raw?: boolean;
}
```

<div className="members-wrapper">

### type

<MemberInfo kind="property" type={`'file'`}   />


### outputPath

<MemberInfo kind="property" type={`string`}   />


### raw

<MemberInfo kind="property" type={`boolean`}   />




</div>


## NoopTransportOptions

<<<<<<< HEAD
<GenerationInfo sourceFile="packages/email-plugin/src/types.ts" sourceLine="238" packageName="@bb-vendure/email-plugin" />
=======
<GenerationInfo sourceFile="packages/email-plugin/src/types.ts" sourceLine="277" packageName="@vendure/email-plugin" />
>>>>>>> upstream/master

Does nothing with the generated email. Intended for use in testing where we don't care about the email transport,
or when using a custom <a href='/reference/core-plugins/email-plugin/email-sender#emailsender'>EmailSender</a> which does not require transport options.

```ts title="Signature"
interface NoopTransportOptions {
    type: 'none';
}
```

<div className="members-wrapper">

### type

<MemberInfo kind="property" type={`'none'`}   />




</div>


## TestingTransportOptions

<<<<<<< HEAD
<GenerationInfo sourceFile="packages/email-plugin/src/types.ts" sourceLine="267" packageName="@bb-vendure/email-plugin" />
=======
<GenerationInfo sourceFile="packages/email-plugin/src/types.ts" sourceLine="306" packageName="@vendure/email-plugin" />
>>>>>>> upstream/master

Forwards the raw GeneratedEmailContext object to a provided callback, for use in testing.

```ts title="Signature"
interface TestingTransportOptions {
    type: 'testing';
    onSend: (details: EmailDetails) => void;
}
```

<div className="members-wrapper">

### type

<MemberInfo kind="property" type={`'testing'`}   />


### onSend

<MemberInfo kind="property" type={`(details: <a href='/reference/core-plugins/email-plugin/email-plugin-types#emaildetails'>EmailDetails</a>) =&#62; void`}   />

Callback to be invoked when an email would be sent.


</div>
