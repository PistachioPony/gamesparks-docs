# SendGrid

[toc]

Provides the ability to send emails via [SendGrid](http://sendgrid.com/).

You need to have already set up a SendGrid account, when acessing send grid via gamesparks you need to provide your sendgrid username & password

e.g.

```
    var mySendGrid = Spark.sendGrid("userName", "password");
```
---

### addTo

*signature* addTo(string email, string name)

*returns* [SendGrid](../Comms/SendGrid)

Adds a recipient to this email

*params*

email - The email address of the recipient

query - The name of the recipient (optional)

*returns*

This SendGrid object

*example*

```
    mySendGrid.addTo("info@gamesparks.com", "GameSparks")
```

---

### send

*signature* send()

*returns* string

Sends this email, this step should be performed after configuring the email fully

*returns*

The response from SendGrid

*example*

```
    mySendGrid.send();
```

---

### setFrom

*signature* setFrom(string email, string name)

*returns* [SendGrid](../Comms/SendGrid)

Sets the from address of this email

*params*

email - The email address of the sender

query - The name of the sender (optional)

*returns*

This SendGrid object

*example*

```
    mySendGrid.setFrom("info@gamesparks.com", "GameSparks")
```

---

### setReplyTo

*signature* setReplyTo(string email)

*returns* [SendGrid](../Comms/SendGrid)

Sets the replyTo address of this email

*params*

email - The email address to replyTo

*returns*

This SendGrid object

*example*

```
    mySendGrid.setReplyTo("info@gamesparks.com")
```

---

### setBcc

*signature* setBcc(string bcc)

*returns* [SendGrid](../Comms/SendGrid)

Sets a bcc address to this email. SendGrid only allows one address in this field

*params*

email - The email address to add as bcc

*returns*

This SendGrid object

*example*

```
    mySendGrid.setBcc("info@gamesparks.com")
```

---

### setSubject

*signature* setSubject(string subject)

*returns* [SendGrid](../Comms/SendGrid)

Sets the subject of this email

*params*

subject - The subject of the email

*returns*

This SendGrid object

*example*

```
    mySendGrid.setSubject("Hello from GameSparks")
```

---

### setText

*signature* setText(string text)

*returns* [SendGrid](../Comms/SendGrid)

Sets the text body of this email. If html is set this value is ignored.

*params*

text - The body of the email

*returns*

This SendGrid object

*example*

```
    mySendGrid.setText("Welcome to using SendGrid via GameSparks")
```

---

### setHtml

*signature* setHtml(string html)

*returns* [SendGrid](../Comms/SendGrid)

Sets the html body of this email.

*params*

html - The html body of the email

*returns*

This SendGrid object

*example*

```
    mySendGrid.setHtml("*Welcome to using SendGrid via GameSparks*")
```

---

### addUploaded

*signature* addUploaded(string uploadId)

*returns* [SendGrid](../Comms/SendGrid)

Adds an uploaded file to the email as an attachment

*params*

uploadId - The id of the uploaded file

*returns*

This SendGrid object

*example*

```
    mySendGrid.addUploaded("7359237762da4245add41e44bc994cdd")
```

---

### addDownloadable

*signature* addDownloadable(string shortCode)

*returns* [SendGrid](../Comms/SendGrid)

Adds an downloadable file to the email as an attachment

*params*

shortCode - The shortCode of the downloadable

*returns*

This SendGrid object

*example*

```
    mySendGrid.addDownloadable("SHORTCODE")
```

---

### addHeader

*signature* addHeader(string key, string value)

*returns* [SendGrid](../Comms/SendGrid)

Adds an custom SMTP header to this email

*params*

name - The header name to set

value - The value to set for the header

*returns*

This SendGrid object

*example*

```
    mySendGrid.addHeader("X-Sent-Using", "SendGrid-API")
```
