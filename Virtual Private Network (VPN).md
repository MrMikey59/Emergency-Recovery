# Virtual Private Network (VPN)

VPNs are all the rage these days, but it's not clear that's for [any
good reason](https://gist.github.com/joepie91/5a9909939e6ce7d09e29). You
should be aware of what a VPN does and does not get you. A VPN, in the
best case, is _really_ just a way for you to change your internet
service provider as far as the internet is concerned. All your traffic
will look like it's coming from the VPN provider instead of your "real"
location, and the network you are connected to will only see encrypted
traffic.

While that may seem attractive, keep in mind that when you use a VPN,
all you are really doing is shifting your trust from you current ISP to
the VPN hosting company. Whatever your ISP _could_ see, the VPN provider
now sees _instead_. If you trust them _more_ than your ISP, that is a
win, but otherwise, it is not clear that you have gained much. If you
are sitting on some dodgy unencrypted public Wi-Fi at an airport, then
maybe you don't trust the connection much, but at home, the trade-off is
not quite as clear.

You should also know that these days, much of your traffic, at least of
a sensitive nature, is _already_ encrypted through HTTPS or TLS more
generally. In that case, it usually matters little whether you are on
a "bad" network or not -- the network operator will only learn what
servers you talk to, but not anything about the data that is exchanged.

Notice that I said "in the best case" above. It is not unheard of for
VPN providers to accidentally misconfigure their software such that the
encryption is either weak or entirely disabled. Some VPN providers are
malicious (or at the very least opportunist), and will log all your
traffic, and possibly sell information about it to third parties.
Choosing a bad VPN provider is often worse than not using one in the
first place.

In a pinch, MIT [runs a VPN](https://ist.mit.edu/vpn) for its students,
so that may be worth taking a look at. Also, if you're going to roll
your own, give [WireGuard](https://www.wireguard.com/) a look.

