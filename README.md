# MailSync
---
Paper: [NDNizing Existing Applications: Research Issues and
Experiences](http://conferences.sigcomm.org/acm-icn/2018/proceedings/icn18-final54.pdf)

## Overview

At the current stage, MailSync is a proof-of-concept application powered by [Named Data Networking (NDN)](https://named-data.net/). 
MailSync project consists of two applicaitons - a laptop version and an Android version. 

- **greenmail-mailsync**: MailSync laptop version
- **mailsync-android**: MailSync Android version

## Test Running

[Demo video](https://youtu.be/wJlEHJROoiY)

### greenmail-mailsync (Laptop version)

Download **activation.jar** and **mail.jar** from this website:

    * https://code.google.com/archive/p/javamail-android/downloads 

Install these two lib locally using Maven:

    * mvn install:install:file -Dfile=/[CHANGE_IT]/activation.jar -DgroupId=javax.activation -DartifactId=activation -Dversion=10.0.0 -Dpackaging=jar
    * mvn install:install:file -Dfile=/[CHANGE_IT]/mail.jar -DgroupId=com.sun.mail -DartifactId=javax.mail -Dversion=10.0.0 -Dpackaging=jar

Download **Thunderbird** mail client from this website:

    * https://www.thunderbird.net/en-US/
    
Configure the **Thunderbird** server settings:

    * Server Name: 127.0.0.1
    * Port: 3143
    * Connection security: None
    * Authentication method: Password, transmitted insecurely

Follow the guide to install [NFD](https://github.com/named-data/NFD) and run it in the background.

### mailsync-android (Android version)

On your Android device, configure your Gmail client incoming server:
    
    * Server name: 127.0.0.1
    * Port: 3143
    * Security: none

Download [NFD](https://play.google.com/store/apps/details?id=net.named_data.nfd) Android version Google Play store and run it in the background.

## Developement

### Technologies involved:
  
  - [NFD](https://github.com/named-data/NFD), [jNDN](https://github.com/named-data/jndn)
  - Email: [Greenmail](https://github.com/greenmail-mail-test/greenmail), [Javamail](https://javaee.github.io/javamail/)
  - Database: [Couchbase](https://www.couchbase.com/) (laptop Java version), [Couchbase Lite](https://docs.couchbase.com/couchbase-lite/2.1/index.html) (Android version)

### Prerequisites

  - Install [NFD](https://github.com/named-data/NFD)
  - Install Javamail as shown above
  - [Maven](https://maven.apache.org/) 
  - [Android Studio](https://developer.android.com/studio/?gclid=Cj0KCQjwpsLkBRDpARIsAKoYI8xmAc7SK6uVyUxP5r-9j_vzg9kQ9X10HzgXirb6SJWkTT31OkvAlFkaAhjlEALw_wcB)

### Current Issues

  - IMAP connection sometimes crashes for unknow reason
  - For the first time a user connects to MailSync on Android, it takes long time to synchronize. The ideal case might be for the first time, MailSync doesn't store all user's emails into database. Only when new emails come in, we store them. 
  - No retransmission mechanism for NDN which causes the whole synchronization failed if a sinlge email chunk get lost.
  - No security mechanims
  - UI/UX to be improved 

Play it, crash it and report more issues on the **Issue** page. 

### Contirbuting

Please read the [NDN Contributing Guide](https://github.com/named-data/NFD/blob/master/CONTRIBUTING.md). 
We are not currently using Gerrit on this project, so that part can be ignored for now. Contributions should follow the [NDN Style Guide](https://named-data.net/codebase/platform/documentation/ndn-platform-development-guidelines/cpp-code-guidelines/).

### Communication

Our chat channel is on [Slack](https://named-data.slack.com/messages)

Please join our mailing list to discuss questions regarding the project: https://named-data.net/codebase/platform/support/mailing-lists/









