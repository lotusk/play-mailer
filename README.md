Note: this release is not yet stable.


Amazon Simple Email Service (SES) module for Play 2.1
=====================================================

Allows you to send email using Amazon SES SMTP


Installation
------------

``` scala
  val appDependencies = Seq(
    "play.modules.mailer" %% "mailer" % "1.1-RC2"
  )
  
  val main = PlayProject(appName, appVersion, appDependencies, mainLang = SCALA).settings(
    resolvers += "Rhinofly Internal Release Repository" at "http://maven-repository.rhinofly.net:8081/artifactory/libs-release-local"
  )
```

Configuration
-------------

`application.conf` should contain the following information:

``` scala
mail.from.name=From name
mail.from.address="validated email address or email adress on validated domain"
mail.smtp.failTo="failto+customer@company.org"

mail.smtp.host=email-smtp.us-east-1.amazonaws.com
mail.smtp.port=465
mail.smtp.username="Smtp username as generated by Amazon"
mail.smtp.password="Smtp password"
```
`application.conf` can additionally contain the following information:
mail.transport.protocol=smtp
mail.smtp.ssl.enable=true

Usage
-----

``` scala
  Ses.sendEmail(Email(
    subject = "Test mail",
    from = EmailAddress("Erik Westra sender", "ewestra@rhinofly.nl"),
    replyTo = None,
    recipients = List(Recipient(Message.RecipientType.TO, EmailAddress("Erik Westra recipient", "ewestra@rhinofly.nl"))),
    text = "text",
    htmlText = "htmlText",
    attachments = Seq.empty))
```

