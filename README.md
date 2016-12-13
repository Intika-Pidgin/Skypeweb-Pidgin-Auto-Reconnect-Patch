# Skypeweb_pidgin_plugin_reconnect_automatically_patch

This patched version (v1.2.2) is intended to fix the network issue where skype does not reconnect automatically...
This is a workaround not an update by any mean !

How to reproduce the bug : connect to skype, cut the internet (without disconnecting the lan network)

The bug : instead of staying disconnected and reconnect when the network come back the account get disabled completely and pidgin automated reconnection does not work anymore, we need to re enable the account manually... in short term the plugin does not reconnect automatically

The quick fix (NOT FINAL !, but working) : under "skypeweb_login.c"
Comment what's under the 3 ifs after "// grab PPFT and cookies (MSPRequ, MSPOK)"
also comment the "Failed getting Magic T value" error and the "return;" after it.

Note : PURPLE_CONNECTION_ERROR_* is not really necessary when network disconnection happen because pidgin itself manage the network connection loss and reconnect on it's own, and even notice it with "ssl connection failed" may be the function need to be rewritten to detect connection loss because for the moment it's confusing skype connection not working and network KO

