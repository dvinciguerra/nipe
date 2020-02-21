<p align="center">
  <img src="https://heitorgouvea.me/images/publications/nipe-overview/logo.png">
  <p align="center">A script to make TOR Network your default gateway.</p>

  <p align="center">
    <a href="https://github.com/GouveaHeitor/nipe/blob/master/LICENSE.md">
      <img src="https://img.shields.io/badge/license-MIT-blue.svg">
    </a>
    <a href="https://github.com/GouveaHeitor/nipe/releases">
      <img src="https://img.shields.io/badge/version-0.9-blue.svg">
    </a>
  </p>
</p>

---


### How it works
```
  The TOR project allows users to surf the Internet, chat and send instant messages anonymously 
  through its own mechanism. It is used by a wide variety of people, companies and organizations, 
  both for lawful activities and for other illicit purposes. TOR is already gone and is used for 
  example by criminal companies, hacking groups, intelligence agencies and even ordinary users who care
  about privacy in the digital world. 
  
  Nipe is a engine, developed in Perl, that aims to make the TOR network your default network gateway. 
  Through Nipe, we can directly route traffic from our computer to the TOR network through which you can 
  surf the Internet having a more formidable stance on privacy and anonymity in cyberspace.
  
  Currently, only IPv4 is supported by Nipe, but we are working on a solution to add IPv6 support. 
  Also, only traffic other than DNS requests destined for local and/or loopback addresses is not 
  trafficked through the TOR. All non-local UDP/ICMP traffic is also blocked by the TOR project.
```


### Download and install:
```bash
  # Download
  $ git clone https://github.com/GouveaHeitor/nipe
  $ cd nipe
    
  # Install libs and dependencies
  $ cpan install Switch JSON File::Which Config::Simple
  $ perl nipe.pl install
```

### Commands:
```
  COMMAND          FUNCTION
  install          Install dependencies
  	  -f           Overwrite Tor config file in /etc/tor/torrc
      -c <file>    Specify a custom location to install Tors config file
  start            Start routing
  stop             Stop routing
  restart          Restart the Nipe process
  status           See status

  Examples:

  perl nipe.pl install -f
  perl nipe.pl start
  perl nipe.pl stop
  perl nipe.pl restart
  perl nipe.pl status
```

It's important to note that inside `.config/` folder there are multiple custom configuration files specificaly
crafted for certain distributions that are used in `install` command; each has its own `User` key, which __should
not__ be changed. The `User` option is the default username used by each distro when their `tor` package gets
installed, thus every personal data (usually placed in `/var/lib/tor` folder or through `DataDirectory` option) is
owned by this user UID:GID.

### Known issues

##### SELinux blocking DNS port setting

For those running a Linux distribution that make use of SELinux strict rules you may need to run the following
command to allow DNS port setting to take effect:

```
# semanage port -a -t dns_port_t -p udp
```

### Contribution

- Your contributions and suggestions are heartily ♥ welcome. [**See here the contribution guidelines.**](/.github/CONTRIBUTING.md) Please, report bugs via [**issues page.**](https://github.com/GouveaHeitor/nipe/issues) See here the [**security policy.**](./github/SECURITY.md) (✿ ◕‿◕) 

- Interested in better understanding how the Nipe really works? Maybe this post can help you: [**A techinical Overview about Nipe.**](https://heitorgouvea.me/2019/11/19/Nipe-Overview)

### License

- This work is licensed under [**MIT License.**](https://github.com/GouveaHeitor/nipe/blob/master/LICENSE.md)