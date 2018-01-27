Configuration
=============

Configuration of all Sandwich Cloud services are managed by environment variables.

Counter - API Server
--------------------

Kubernetes
^^^^^^^^^^

:code:`KUBECONFIG`
  Path to a Kubernetes client configuration file to communicate with a Kubernetes
  Cluster. If not given will default to using the in-cluster configuration.

:code:`KUBEMASTER`
  The address of the Kubernetes API server. This will override any value that is
  set in the :code:`KUBECONFIG`

Authentication
^^^^^^^^^^^^^^

:code:`AUTH_FERNET_KEYS`
  A url safe 32-bit base64 encoded string used to encrypt user tokens. Multiple
  keys can be listed to allow rotation (comma separated). The first key in the list
  is the primary key. To rotate keys simply generate a new key and put it in the
  front of the list, then after a while remove the old key from the list.

:code:`AUTH_DRIVERS`
  A python module path to a class that implements an auth driver. Multiple auth
  drivers can be given as a comma separated string. The first driver in the list
  is considered the default auth driver that clients will default to. If no drivers
  are given it will default to the Database Driver.

  Driver Paths:
    * Github: deli.counter.auth.drivers.github.driver:GithubAuthDriver
    * Database: deli.counter.auth.drivers.database.driver:DatabaseAuthDriver

Database Auth
~~~~~~~~~~~~~

These configuration items are only needed when using database authentication.

:code:`DATABASE_DRIVER`
  The database driver to use to connect. Some drivers may require additional python
  libraries to work.

  Valid Supported Values:
    * postgresql
    * mysql
    * sqlite

:code:`DATABASE_DB`
  The name of the database. If using sqlite this is usually the path to the
  sqlite file.

:code:`DATABASE_HOST`
  The address of the database host

:code:`DATABASE_PORT`
  The port used to connect to the database host

:code:`DATABASE_USERNAME`
  The username used to connect to the database

:code:`DATABASE_PASSWORD`
  The password used to connect to the database

Github Auth
~~~~~~~~~~~

These configuration items are only needed when using github authentication.

:code:`GITHUB_URL`
  The Github API url. Defaults to the public Github API url.

:code:`GITHUB_CLIENT_ID`
  The client ID used to authenticate to the Github API

:code:`GITHUB_CLIENT_SECRET`
  The client secret used to authenticate to the Github API

:code:`GITHUB_ORG`
  The github organization users must be part of. This organization is also used
  to check user teams.

:code:`GITHUB_TEAM_ROLES`
  A static mapping of sandwich cloud global roles to github teams. These static
  mappings will override GITHUB_TEAM_ROLES_REFIX if a role is found.

  Examples:
    * :code:`admin:sandwich-admin`
        * A Github team called :code:`sandwich-admin` will be mapped to the global role called :code:`admin`.
    * :code:`role1:sandwich-role1`
        * A Github team called :code:`sandwich-role1` will be mapped to the global role called :code:`role1`.

:code:`GITHUB_TEAM_ROLES_PREFIX`
  Prefix to use when searching for Github teams. If no static mapping for a role
  is given this prefix will be used.

  Example:
    * :code:`sandwich-`
        * For a Github team called :code:`sandwich-role1` a global role with the name of :code:`role1` will be given to the user.

Manager - Resource Controller
-----------------------------

Kubernetes
^^^^^^^^^^

:code:`KUBECONFIG`
  Path to a Kubernetes client configuration file to communicate with a Kubernetes
  Cluster. If not given will default to using the in-cluster configuration.

:code:`KUBEMASTER`
  The address of the Kubernetes API server. This will override any value that is
  set in the :code:`KUBECONFIG`

VMware VCenter
^^^^^^^^^^^^^^

:code:`VCENTER_HOST`
  The address used to connect to the VMware Vcenter server

:code:`VCENTER_PORT`
  The port used to connect to the VMware Vcenter server

:code:`VCENTER_USERNAME`
  The username to authenticate with against the VMware Vcenter server

:code:`VCENTER_PASSWORD`
  The password to authenticate with against the VMware Vcenter server

Menu
^^^^

:code:`MENU_URL`
  The telnet url of the Metadata Service.

  For SSL connections use the following format: telnets://<host>:<port>#key[=value][&key[=value] ...]
    * thumbprint=value
        * Specifies a certificate thumbprint against which the peer certificate thumbprint is compared. When you specify a thumbprint, certificate verification is automatically enabled. See the description of the verify parameter below.
    * peerName=value
        * Specifies the peer name that will be used to validate the peer certificate. When you specify a peer name, certificate verification is automatically enabled. See the description of the verify parameter below.
    * verify
        * Forces certificate verification. The virtual machine will verify that the peer certificate subject matches the specified peerName and that it was signed by a certificate authority known to the ESXi host. Verification is automatically enabled if you specify a thumbprint or peerName.

Menu - Metadata Service
-----------------------

Kubernetes
^^^^^^^^^^

:code:`KUBECONFIG`
  Path to a Kubernetes client configuration file to communicate with a Kubernetes
  Cluster. If not given will default to using the in-cluster configuration.

:code:`KUBEMASTER`
  The address of the Kubernetes API server. This will override any value that is
  set in the :code:`KUBECONFIG`

Authentication
^^^^^^^^^^^^^^

:code:`FERNET_KEY`
  A url safe 32-bit base64 encoded string used to encrypt service account tokens.
  This must match a fernet key that the API Server uses.
