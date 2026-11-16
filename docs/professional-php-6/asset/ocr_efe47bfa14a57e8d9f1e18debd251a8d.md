```
"last_name" character varying (255),
"email_address" character varying(256) NOT NULL,
"date_of_signup" date NOT NULL,
"time_of_signup" time NOT NULL,
"remote_addr" character varying(15) NOT NULL
);

GRANT ALL PRIVILEGES ON "subscriber" TO "newsletter";
GRANT ALL PRIVILEGES ON "subscriber_id_seq" TO "newsletter";

CREATE UNIQUE INDEX "em_unq_idx" ON "subscriber" ("email_address");
```

That unique index at the end isn’t strictly necessary, as you’ll be sense-checking to ensure that the current subscriber does not exist as part and parcel of your data input validation; but it’s good from a belt-and-braces point of view. Should you ever want to extend your application to allow data manipulation from a third-party source, the uniqueness of your subscriber database can be guaranteed.

# An Example Application

With your sample database in place, it’s now time to start looking at some individual frameworks. They all seek to achieve much the same goal, but they all approach it slightly differently. Like boxers versus briefs versus going “commando,” a lot of it comes down to personal preference.

Let’s start by looking at a complete application written in a newcomer PHP framework developed especially for PHP 6 — Ulysses.

# Introducing Ulysses

Ulysses is an open-source, object-oriented PHP application development framework available free under the BSD (Berkeley) license. This means that regardless of the ultimate goal of your project (altruistic, commercial, or downright Mephistophelean), it’s free to download, use, and deploy. Support and documentation is available on a commercial basis.

# Installing Ulysses

To download Ulysses, visit the project’s Web site at www.ulyssesframework.com. You’ll be redirected to the project’s home page on SourceForge, from which you can download the latest version.

Move the downloaded .tgz file into /usr/local/lib/php — or wherever your PHP libraries are normally kept. Then, unarchive it using the following standard syntax:

```
tar -xzvf ulysses-3.0.23.tar.gz
```