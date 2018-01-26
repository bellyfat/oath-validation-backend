# oath-validation-backend
Oath validation server for HOTP and/or TOTP using sqlite3 as backend

This is a small server for validating oath, hotp (counter based) and totp (time based) one-time passwords (OTP). 

The idea is to mimic how pyhsm from Yubico does the OATH validation with their YubiHSM but without the actuall HSM.
Why? Because I needed to test the functionallity without the cost of a HSM. This is also why Yubicos copywrite is in the
files, please respect that. 

With that said keep in mind that the "secret" of the OATH is stored in cleartext in the sqlite database. 
If you want a more secure solution consider buying a YubiHSM or perhaps use sqlcipher to encrypt the sqlite database. 

There are quite a few dependencies of other python modules which you can find in the import statements in the files.

License
The project is licensed under the BSD license, see the file COPYING for exact
wording.


* soft-validation-server:

the web based server taking the oath requests and validates them.

usage: 

soft-validation-server.py [-h] [--debug] [--hotp] [--totp]
                                 [--db-file FILENAME] [--port PORT] [-v]
                                 [--addr ADDR] [--hotp-window NUM]
                                 [--totp-interval NUM] [-U SERVE_URL]
                                 [--totp-tolerance NUM]

* soft-init-oath-token:

a tool to provision the sqlite database with the userid needed to identify which "secret" to use. 

usage: 

soft-init-oath-token [-h] [-v] [--debug] [--force] --uid STR
                            [--oath-c INT] [--oath-k HEXSTR] [--db-file FN]
