I stalk your github
===================

That could be an upsetting headline, couldn't it? Well I hope it's clear from
what I do with that information that my intentions are benign-to-benevolent.
I spend a few hours a week feeling pretty creepy about myself as I follow the
details of your work pretty intently. Every Saturday I curate new videos for my
youtube playlist, which at the first of the month I re-download and mirror
locally to my Plex. Underneath that part of the Plex library is a Syncthing
share, on that share are two stripped-down, deactivated burner phones and a
travel router sporting 64GB SD cards, all synced over i2p tunnels. Along with
some cartoons. Pretty sure the Catherine Zeta-Jones version of "The Haunting"
for some reason. Since I don't use a mobile, I take one of these devices pretty
much everywhere. On that same group of Syncthing instances is another share,
which has every academic paper or infographic on i2p I could source from
anywhere I could think of. If you can think of an image search engine, I've
typed "i2p" into it and downloaded every one that wasn't outwardly stupid. And
of course, everyone who's contributed to i2p, i2pd, or Kovri on Github and
increasingly, Gitlab? I keep up with your work, at least if it goes on that
platform. I'd be willing to bet that I know as much or more about i2p than
anyone who doesn't work on one of the routers. What I'm trying to say is that
I'm your biggest fan.

I don't exactly have much to declare in this part, it's more of a post-facto
diary to help you see how my use of i2p has shaped my perspective upon it. Parts
two and three have more precise points.

I guess it started with SSH, if I think about it
------------------------------------------------

Guess what? I'm pretty broke. Like, American poor, so bad but not
literally at risk of dying this month from exposure or starvation-related
reasons. So I guess there's that. I work the night shift at a hotel that expects
me to clock out for a break which they expect me not to take. But poor people
tend to have older equipment. My laptop was first sold in 2007, it is now 2018.
It takes roughly 8 1/2 hours to compile [my coreboot experiments](https://github.com/eyedeekay/vendor)
on it. I can take it to work, start compilation, and fail once. But for
desktops, man, it's a buyer's market if you pay attention. Go on ebay the right
day, you can get something that'll reduce that to about an hour for like 40
bucks. But try carrying that motherfucker with you to work. If you think that's
possible to do safely, you're living in a different bubble than me that's all
I'm saying.

So I need to be able to talk to the desktop, which is at home, from the laptop,
which I take with me to work. In order to do that well, I need to be able to
consistently address my desktop regardless of where I am, and I'd like to not
have to depend on a dynamic DNS service to do so, and not have my ISP know that
I'm running an SSH service out of a Debian box in my bedroom. When I started
doing this there was no Kadnode and cjdns was new and, perhaps correctly, a
little uptight when it came to amateurs like me. But i2p had been around for
years, and str4d had already answered a Server Fault question to exactly this
effect. So I turned down the tunnel length, forwarded port from the localhost to
port 7622 on i2p. Then I copied the client keys into the server whitelist, and
the server keys into the client's whitelist, and thought to myself:

  *"self, isn't this pretty much a way to account for the two things that SSH*
  *doesn't do?"*

  *"remind me what those thing are, self?"*

  *"Well, ssh doesn't think it's possible for it itself to prevent leaks of*
  *host names and stuff lke that, which is probably true, and it relies on*
  *the initial key exchange to verify that you the client are connecting to*
  *the server you intend to"*

  *"Self, I think you might be on to something. Because you're using i2p*
  *tunnels with a whitelist on both ends, only an authentic client can connect*
  *to the authentic server tunnel, and this extends logically to the SSH server*
  *and client. So if someone doesn't have your SSH client keys, "they" can't*
  *try and determine your host name by attacking your SSH server, because*
  *unless you have the client tunnel keys, you can't even tell what's running.*

  *"Pretty cool huh, self? Moreover, you use the i2p hostname to address the*
  *SSH server now, which is itself cryptographically authenticated. So you can*
  *use when you're authenticating new devices.*

  *"Wow that's pretty neat."*

  *"Those i2p people are clever."*

  *"College is fun."*

That was years and years ago, before Oxy* and even Mosh maybe. Not even sure if
Mosh tries to solve the privacy stuff either, and I don't use Oxy yet, mostly
because I like my ssh-over-i2p tunnels so much. But for a long, long time, I
didn't get much more creative than adding devices to my tunnel-cloud. But like,
more than a decade ago you could do that with i2p. I'm not even if Tor hidden
services had that kind of whitelisting at that point. From a guy who just wants
an easy, reliable way to SSH to his house, that's fucking awesome.

* the ssh replacement, not the pill. Not into pills. Fuck Mylan.

No wait, I think it might have been apt?
----------------------------------------

I know this was a long-ass time ago, because it was when I still had a Facebook,
which has been like, a qoddamn long-ass time. But at the time I was a member of
a short-lived user group that decided to collaborate on their own Debian spin.
I slogged my way through the live-build documentation and at some point ran into
something wierd, which I think may have been taken down, and which I haven't
seen anywhere but my own github repositories since. It turns out it's pretty
easy to host a package repository in a github page. They're both just kinds of
static sites, after all. But it seemed like a *super* obnoxious thing to do on
a git hosting site, so I decided I would try and host it on something where I
was contributing to the bandwidth and all the storage which would be used to
make the packages available to download. So I searched around for a static site
server, after a few false-starts I used lighttpd for years, and the script that
set up your repository could optionally point your eepsite tunnel at the local
http service instead of jetty.

At first, I used it to store the lua scripts that I use to configure AwesomeWM
as their own packages, with one big meta-package to install them all. Because
I'm a crazy person who gets very bored at his night job. So bored.

So very bored.

Then I added those repositories to the live-build configuration, and holy shit,
I had a spin of Debian which configured all my preferred software in advance,
I could run it off the USB drive or I could install it from the USB drive. It
even has a persistence volume. Most of the time, I can just plug it into a
computer and have my whole environment. Which is where I started thinking about
other things I could do with i2p to make my environment even more mobile without
sacrificing privacy or control over my own data. But, and maybe here's the whole
point, *configuring the web interface doesn't scale to the idea that I had*. So
I set up the server, isolated the configuration changes that I needed to make,
and set about packaging them in every kludgy, awful way I could. My mantra was
"keep stable, test on the laptop, keep a backup USB ready, upgrade the configs
last."

*Also Microsoft owns github now. Redundancy was previously a fringe-benefit. Now
it's a thing I'm looking forward to gloating about in the future.

Here's the thing
================

I had realized some of the incredible versatility of this remarkable software,
and was doing really obnoxious things to myself to configure it because I didn't
really understand how to do it without the web interface. I'm probably just
a little lazy. XML makes my eyes hurt. I kept it all running by being really,
really careful and doing very, very diligent backups. That's still a whole lot
of work. And then along came i2pd. Fucking ini files? Now we're talking. I
switched my server over to i2pd and started gleefully deleting sed scripts. I
mean gleefully, I got fuckin' enthusiastic. I finally had a reliable way to add
every little gadget I had to my i2p-based cloud, as long as I modified my
repository hosting infrastructure to support Android. If, by this point, you're
wondering why I haven't mentioned garliccat yet, I'll get to that in the third
part. But then I stopped using my custom Android apps and switched to Debian on
an Allwinner tablet, because I'm reckless amateur with a toxic mixture of
curiosity and control issues. But the arrangement still wasn't perfect, and I
still hadn't written a single SAM application yet.

Then somebody talked some shit on reddit
----------------------------------------

All this cool shit I was able to do with i2p made me want to give something else
back to the i2p community. At some point I had picked up Go development, and
fallen in love with it like I love i2p, so I figured I would try and contribute
to a Go library for writing applications that use i2p for something. So I put
"i2p language:Go" into github search and saw that goSam had the shorter
example, so I started with it. About that same time, [this reddit post](https://www.reddit.com/r/i2p/comments/579idi/warning_i2p_is_linkablefingerprintable/)
was made. I already knew that, I'd read the manual after all, but I did think
that OP had a point when it came to somebody who was actively trying to link
your i2p destinations to another identifier, like a social media account or
a browser fingerprint. And goSam was an obvious tool to solve this problem(I
thought) so I started writing it, then I got a second job, forgot what I was
doing, came back to it, realized that it would close the tunnel if the SAM host
wasn't the local host(I had i2pd running in a docker container at this point)
and attempt to re-open it with the localhost, even if there was no SAM port
available. So that was the first or second contribution I made to goSam, and
at that point, I could pretty much make sure that you had a different tunnel ID
for every eepSite you visited. Along with first-party isolation and fingerprint
protection, it can probably provide some defense against malicious groups of
eepSites. And in order to test it, I made it super, super easy to set up
malicious groups of eepSites. Unfortunately, it's inescapably easy to determine
that the isolated destinations are in use by determining that a request to a
third-party resource doesn't occur with the same destination, so they know you're
running it. But that information is even less useful than a throwaway
destination like in default i2p if as I suspect, somewhat more people are taking
an interest in it against my explicit recommendations(about half kidding, it
does what it says and doesn't leak anything new except that it's in use. I use
it. I test and attack it too. Pretty sure it's fine). So I bit off more than I
could chew with my first i2p app, and ended up more-or-less porting a feature
of Tor to i2p without needing to touch the actual i2p router, and once I
got the hang of it, it got me to my real point, which is that **developing i2p**
**apps is super easy, and it's easy to make i2p deliver useful things that**
**are impossible to get in other ways.** New app developers need help realizing
this, and they can help you break the can opener back out of the can, to borrow
a phrase. I'll leave it there for now, in the next one I'll talk about bringing
the swiss-army knife.
