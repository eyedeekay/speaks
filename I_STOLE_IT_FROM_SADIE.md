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

The problem of a "can opener inside the can" is actually theoretically
imaginary. It's a hypothetical problem. If you have a can of can-opener in the
real world, you just look for another can-opening utensil. Like a Swiss-Army
knife. Busybox has been called the Swiss-Army Knife of Embedded Linux. I think
i2p needs it's busybox. I think Tor needs it's busybox too, actually. The
busybox of darknet interaction may not need to be as extensive as BusyBox or
Coreutils, for instance, but there are a few obvious things it could use.

### netcat for the i2p network

[My take on the matter is compatible with i2pd configuration files](https://github.com/eyedeekay/sam-forwarder)

### apt-transport-i2p

[rationalize apt-transport-i2p here]

### dig for the i2p network

[because why not]

### curl for the i2p network

[present iget here]

[explain my issues with eepGet]

### mktorrent for i2p

I haven't made anything like this yet, but it's probably easy-ish.

### turnkey, embeddable DHT-over-i2p

Neither this, but less easy.

### proxy multiplexer for bridgable applications

How to make it super easy to make SyncThing i2p-native.

The Matter of Content
---------------------

Another reason that application development is important is that in many cases,
it can help make more content available to people who would prefer to access it
via i2p. An example would be ZeroNet's choice to integrate with the Tor network,
which has resulted in an explosion of persistent content available via ZeroNet
over Tor. Now most of ZeroNet outside the forums is a badlands of the
useless-to-vile(The tech is cool but holy fuck is it easy to find some wicked
shit there), but it's ability to host persistent, distributed forums is pretty
cool and something that i2p could use.

### I'm not saying ZeroNet, yet, but for ironic and inadequate reasons

One of the things I like most about i2p is that in spite of it's occasional
willingness to use stereotypically villainous imagery to satirize the alarmist
coverage of the "Dark Net" in popular culture, the actions of the project and
it's participants are pretty pro-social. I can honestly say that in over a
decade of i2p use, I've never encountered material that was illegal in my
country. I've encountered ways of acquiring legal material that under some
circumstances could lead to civil liability, but not once have I encountered
anything infamous. Not so for ZeroNet. It's so easy to make nasty shit really,
really permanent and really, really public on ZeroNet that it may push the
barrier to entry too far in favor of the pedophiles. I say, let ZeroNet sort out
it's community first, and see what happens later. Instead, focusing on things
like Aktie, Syndie, Nightweb, and maybe even porting Aether to be i2p-native
would be better options for what I see as the chief benefit of ZeroNet, which
is the ability to create un-hosted community forums.

### Podcasts, XD, and something for Humans



### Interplanetary Filesystem

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

