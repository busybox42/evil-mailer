# evil-mailer
This repository contains a mailer script I wrote in ruby.

## Requirements
Ruby gems mail and parallel:

https://rubygems.org/gems/mail

https://rubygems.org/gems/parallel

## Useage
```bash
Usage: mailer.rb [options]

    -t, --to user@domain.tld         Email address to send to.
    -l, --list list.txt              List of Email address to send to.
    -f, --from user@domain.tld       Email address to send as. Default: postmaster@evil-admin.com
    -n, --name 'Name'                Sender's name  Default: 'postmaster'
    -s, --subject 'Subject Text'     Subject header of the email. Default: 'This Is A Test'
    -x, --text message.txt           Text message to send. Default: message.txt
    -w, --html message.html          HTML message to send. Default: message.html
    -H, --host smtp.hostname.tld     SMTP host to send. Default: 127.0.0.1
    -p, --port smtp port             SMTP port to connect to. Default: 25
    -A, --auth (plain|login)         SMTP authentication type. Default: login
    -T, --threads #                  Number of parallel threads. Default: 1
    -g, --log file.log               Write to log a file. Default: /tmp/mailer.log
    -U, --user username              SMTP auth username
    -P, --pass username              SMTP auth password
    -o, --helo host.domain.tld       HELO string, ussually a hostname
    -d, --header X-Header1 Value     Comma seperated additional headers
    -a, --attach /path/to/file1.ext  Comma seperated attachments
    -r, --random /path/to/messages   Directory of random html and text messages.  This is typically used to load test a mail system.
    -L, --tls                        Enable STARTTLS.
    -h, --help                       Usage options.
```
## Examples
Basic Example:
```bash
./mailer -t user@domain.tld -f user@domain.tld -s 'Test Message'  -x message.txt -w message.html -H 127.0.0.1 
```
Auth User Example:
```bash
./mailer -t user@domain.tld -f user@domain.tld -A login -U user -P password -s 'Test Message'  -x message.txt -w message.html -H 127.0.0.1
```
Threaded List Sending Example:
```bash
./mailer -T 10 -l list.txt -f user@domain.tld -s 'Test Message'  -x message.txt -w message.html -H 127.0.0.1 
```
