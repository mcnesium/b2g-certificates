b2g-certificates
================

A shell script to add root certificates to Firefox OS

*The script originates at Enrico's [pending.io](http://www.pending.io/add-cacert-root-certificate-to-firefox-os/) where the discussion came up to enhance the script. The following is the initial documentation taken from that page as well. Anyone is welcome to contribute.*

While being quite happy with my new Firefox OS phone so far, the biggest stopper for me was that, like all Mozilla products, the root certificate of [CAcert](https://www.cacert.org) was not included and so I could not access sites using certificates assured by CAcert.

Recent versions of [Gaia](https://github.com/mozilla-b2g/gaia) allow to accept untrusted site certificates in the browser but in case you want to use an IMAP server or Caldav server which is using a CAcert assured certificate, you are still stuck.

Based on a post by [Carmen Jiménez Cabezas](https://groups.google.com/forum/?fromgroups#!topic/mozilla.dev.b2g/B57slgVO3TU), I wrote a script to read the certificate database from the phone (via adb), add some certificates and then write the database back to the phone. After this procedure, the CAcert root certificate (or any other) are known by the phone and can be used. This enabled me to access my own IMAP server via SSL from the Email app and also use a self-hosted groupware as Caldav server for the Calendar app via HTTPS.

How-to
------

Save the script somewhere on your system.

Once done, add a new directory in the directory where you stored the script and place the certificates which you want to add to the phone's database in the sub directory 'certs'. For CAcert, this would be the class 3 root certificate in PEM format as found on the [CAcert website](https://www.cacert.org/index.php?id=3).

Then simply run the script.

Note: before running the script you need to enable 'Remote debugging' in the Developer settings menu and connect your phone with your PC using a USB cable (or more general: get adb working).
