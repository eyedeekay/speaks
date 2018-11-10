Getting the can-opener out of the can, hosting edition
======================================================

Hosting one or two applications by adjusting the web interface in regular i2p,
or by adjusting i2pd's ini files and restarting, but once you start doing more
than a few, it becomes tedious and you have to think about things like what
devices you are going to kick off when you restart the router. The wizard is
great at guiding a user through the steps of forwarding a local service to i2p
in almost all straightforward cases, but it comes with defaults that might not
be optimal for popular applications and once somebody gets bogged down in the
elaborate tunnel configuration Web interface, it can be quite confusing. People
don't like to "Dial in" their secure software. Here, it's possible for
experienced i2p users to make a difference outside of the core router and grow
the pool of available i2p knowledge and tools.

Encapsulating Configuration
---------------------------

Very recently, the i2pd router did another thing for how it is configured that
pleased me immensely, they started using a conf.d directory instead of a
monolithic tunnels.conf file. This is *incredibly* convenient for sysadmins who
wish to make content available on i2p in particular because it allows you to
distribute ready-made tunnels.conf fragments, which pre-configure specific
services. You could even distribute them as packages and install them with

        sudo apt-get install i2p-ssh-config

for example, it could easily install the ssh configuration to the conf.d folder
without requiring the regular tunnels.conf to be changed. Then every sysadmin
who wants it can have **zero-conf, self-addressing, self-authenticating hidden**
**SSH services** in a matter of seconds. How's that for getting the canopener
out of the can, to borrow a phrase from your recent tweets?

This same methodology could be applied to basically any service. For instance,
at home, I host a web interface to Youtube-DL which I attempt to encourage my
room mates to use. It automatically adds videos that we watch to the self-hosted
video service. Since my primary use case for i2p is to control my home PC from
work, this is a service which it would be logical to encapsulate for use with
i2p. Then I can just visit it from the Firefox/i2p browser on my tablet and
download videos I watch at work to the backup storage at home.

Unfortunately, it only works for i2pd right now, and only since recently. Or
does it...

Bringing the Swiss-Army Knife
-----------------------------

I think i2p needs it's busybox. I think Tor needs it's busybox too, actually.
The ability to dynamically put up and tear down hidden services of both types
is valuable for many reasons. In order to do this, I started experimenting with
the SAM API for configuring tunnels that work like regular i2ptunnel, to that
end creating sam-forwarder(the binary it produces is called "samcatd").

The Matter of Content
---------------------

Another reason that application development is important is that in many cases,
it can help make more content available to people who would prefer to access it
via i2p. An example would be ZeroNet's choice to integrate with the Tor network,
which has resulted in an explosion of persistent content available via ZeroNet
over Tor. Now most of ZeroNet outside the forums is a badlands of the
useless-to-vile, but it's ability to host persistent, distributed forums is
pretty cool and something that i2p could use.


Considering an idealized i2p-native remote-access tool
------------------------------------------------------


Current and Specific Criticisms of the API's available
------------------------------------------------------

### The in-i2p Human-Readable, Self-Administered Address Book isn't ambitious enough


###

GarlicCat could be cooler
-------------------------


Can a router be "Just SAM?"
---------------------------

