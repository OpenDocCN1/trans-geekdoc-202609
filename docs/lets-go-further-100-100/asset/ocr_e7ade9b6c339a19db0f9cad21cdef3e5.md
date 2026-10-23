```
```bash
$ mkdir -p remote/setup
$ touch remote/setup/01.sh
```
```

Then add the following code:

```
```bash
File: remote/setup/01.sh

#!/bin/bash
set -eu

#
====================================================================
======= #
# VARIABLES
#
====================================================================
======= #

# Set the timezone for the server. A full list of available timezones can be found by
# running timedatectl list-timezones.
TIMEZONE=America/New_York

# Set the name of the new user to create.
USERNAME=greenlight

# Prompt to enter a password for the PostgreSQL greenlight user (rather than hard-coding
# a password in this script).
read -p "Enter password for greenlight DB user: " DB_PASSWORD

# Force all output to be presented in en_US for the duration of this script. This avoids
# any "setting locale failed" errors while this script is running, before we
```
```