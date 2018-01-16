This is a workaround for a major network issues students at
Brigham Young University Idaho often experience. Users will connect to the
network via wifi and be provided proper Internet access for a period of time.
After an inconsistent amount of time, the users will still be connected to the
network, but will not have access to the Internet outside the network.

This script detects when access to the Internet has been lost and will
automatically tell network manager to reconnect to the network. This makes for
a nearly seamless fix.

To install, move byui-patch-wifi to the directory '/etc/network/if-up.d'. You
will need root permission to do this. Remember to give the script execution
permission as well. This script will execute whenever you connect to any
network, but will immediately exit if it is not a BYUI network.

The following commands will do this.
```
sudo mv byui-patch-wifi /etc/network/if-up.d
sudo chmod a+x /etc/network/if-up.d/byui-patch-wifi
```

Move byui-patch-down to '/etc/network/if-post-down.d'. You will need root
permission to do this. Remember to give the script execution permission as
well.  This script will execute whenever you disconnect from any network. It
kills the byui-patch-wifi script on disconnect.

The following commands will do this.
```
sudo mv byui-patch-down /etc/network/if-post-down.d
sudo chmod a+x /etc/network/if-post-down.d/byui-patch-down
```
