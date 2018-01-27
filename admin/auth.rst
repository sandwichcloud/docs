Authentication
==============

Fernet Keys & Tokens
--------------------

Sandwich Cloud uses `Fernet <https://cryptography.io/en/latest/fernet/>`_ tokens
for authorization. These tokens require a key to be encrypted. The key must
be a 32-bit base64 encoded string. Multiple Fernet Keys can be used to allow key
rotation.

These tokens contain information about the user or service account and what roles
they have access to. User tokens expire one day after they are generated while
service account tokens expire 30 minutes after they are requested from the Metadata
service.

Drivers
-------

There are many ways to authenticate to Sandwich Cloud. Authentication is pluggable
and is handled by drivers.

Database
^^^^^^^^

The Database driver authenticates users against a database that is managed by
Sandwich Cloud.

Github
^^^^^^

The Github driver authenticates users against public GitHub or a private Github
Enterprise installation.

Gitlab
^^^^^^

Not implemented

LDAP
^^^^

Not implemented

OpenID
^^^^^^

Not implemented
