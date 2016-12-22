# DCSS public server autologin script #

This bash script uses GNU screen to facilitate automated logging into
dgamelaunch-based public DCSS *console* servers (webtiles do not need this
as they can use the browser's facilities).  The script is configured by
using environment variables.  I recommend creating small shell script
similar to this:

    #!/bin/bash
    
    env \
      DCSS_TERM=putty-256color \
      DCSS_SCRNO=12 \
      DCSS_HOST="crawl.akrasiac.org" \
      DCSS_USER="MyUserName" \
      DCSS_PASS="Pa$$w0rd123" \
      dcss-autologin

Note, that SSH client must be configured so that it asks *no* questions
during establishing the session.  That means that you must setup pubkey
authentication (and the server must support it).

The variables explained:

* **DCSS_TERM** is terminal type.
This variable is optional and can be used terminal type to be used
with the new screen session in which the game is started.

* **DCSS_SCRNO** is GNU screen's window number.
You must use unused window, so choose something higher,
like above 10 or so, to avoid conflicts.

* **DCSS_HOST** is hostname of the DCSS server
or SSH alias (configured in `.ssh/config`).

* **DCSS_USER** is your player name on the server

* **DCSS_PASS** is your password on the server
