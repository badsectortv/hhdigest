Happy Hacker posts: Aug. 1996

(If you happen to have copies of posts that aren't here, please email them to cmeinel@techbroker.com for inclusion.) 
 

Date: Mon, 5 Aug 1996 12:12:37 -0600 (MDT) 
From: "Carolyn P. Meinel" <cmeinel@techbroker.com> 
X-Sender: cmeinel@plato.nmia.com 
Subject: Free clues

Here's a little more homework on telnetting to specific port -- and some 
totally *free* clues!

For the time of day and date here in New Mexico,

telnet home.nmia.com 13

And for a good time,

telnet home.nmia.com 19

For those of you waiting with breathless anticipation for the next 
installment of the Guide to (mostly) Harmless Hacking, hang on just a 
bit. The next issue, which tells you how to get a finger command *around 
a firewall* that would normally block finger, is under review by an 
Uberhacker to ensure that it is absolutely technically accurate.

Two people have emailed me convincing evidence of commission of crimes. 
They expected me to admire their innate |<-radness.

Clue 1: What if this were a sting operation?

Clue 2: You sent it unecrypted. Guess what, anyone with root access to 
the computer hosting my shell account could also read your email. Guess 
what, the owner of my ISP detests hackers and would not hesitate to throw 
you in jail. And he is a major Unix wizard!

Clue 3: One correspondent expected me to be impressed that he knows how 
to impersonate a telephone solicitor in order to get people to give him 
credit card numbers. Guess what, the average telephone solicitor has an 
IQ of about 80 and makes somewhere around minimum wage. Wow, am I 
impressed that this guy is such a brilliant social engineer that he can 
imitate those kewl d00dz!

Clue 4: This is a list for *legal* hacking. The internet and Unix are so 
incredibly amazing, we could hack for the rest of our lives without 
running out of legal, phun stuph.

>Date: Wed, 28 Aug 1996 13:48:58 -0500 (CDT) 
>From: "T.Q.D.B." <tqdb@wichita.fn.net> 
>Subject: Re: Message from Internet

>On Wed, 28 Aug 1996, Dale Amon wrote: 
> 
>> I applaud Carolyn's efforts in this area. She is absolutely right. Spammers are 
>> controlled by the market. If enough people are annoyed, they respond. If that 
>> action causes problems for an ISP it puts it in their economic interest to 
>> drop customers who cause such harm, ie the spammers. Economic interest if often 
>> a far stronger and much more effective incentive than legal requirement. 
> 
>    From what I've seen and read, most 'professional' spammers know the 
>accounts are going to be terminated and treat them as such.  They 
>typically don't ask you to respond to their email address, but instead 
>give an 800 number, web site or other contact information.  Such was the 
>case a few months ago when a person spammed Usenet from our ISP.  We 
>immediately terminated the account, but there wasn't any way to retract 
>the damage (I suppose we could have ran a cancelbot, but that aside..). 
>There really isn't any way for an ISP to prevent spams without going 
>through a lot of reprogramming and trouble. 
> 
>    Probably the most ironic spam that I've ever seen was when a 
>competing local ISP decided to send spam through email (without the 
>decency to even do a BCC) to our users advertising the opening of their 
>new Internet store.  Needless to say, I wrote back a letter explaining 
>how I would use every ounce of my influence to spread the word that if 
>their Internet store wasn't even good enough for the owner to know 
>netique, that no one should bother going there.  I also sent back 5 copies of 
>the message to the sender's account.  An associate of mine just decided 
>to set up a cron job that would email a copy of the message to them every 
>5 minutes and let it run for a week or so.  Each to his own I guess. 
>.TQDB 
> 
> -=| T.Q.D.B. - tqdb@wichita.fn.net - http://www.feist.com/~tqdb |=- 
> 
>        "A small percentage of them give the rest a bad name. 
>          The term 'hacker' is not necessarily derogatory." 
>      --Special Agent Andrew Black, FBI SF Computer Crime Squad 
> 
> 
> 
Thu Aug 29 20:42:21 1996 
From: "Carolyn P. Meinel" <cmeinel@techbroker.com> 
Subject: Happy Hacker: Nslookup

Here's a quick run down on another command that can help you track down spammers -- and do other kewl stuph, too.

Please note that Terry has provided us with an UNDOCUMENTED FEATURE of nslookup. Enjoy!

>From: Terry McIntyre <tm@proxy2.switch.com>

> 
>nslookup 
>>help 
> 
>Commands:       (identifiers are shown in uppercase, [] means optional) 
> 
>NAME            - print info about the host/domain NAME using default server 
>NAME1 NAME2     - as above, but use NAME2 as server 
>help or ?       - print help information 
>exit            - exit the program 
>set OPTION      - set an option 
>    all         - print options, current server and host 
>    [no]debug   - print debugging information 
>    [no]d2      - print exhaustive debugging information 
>    [no]defname - append domain name to each query 
>    [no]recurse - ask for recursive answer to query 
>    [no]vc      - always use a virtual circuit 
>    domain=NAME - set default domain name to NAME 
>    root=NAME   - set root server to NAME 
>    retry=X     - set number of retries to X 
>    timeout=X   - set time-out interval to X 
>    querytype=X - set query type to one of A,CNAME,HINFO,MB,MG,MINFO,MR,MX 
>    type=X      - set query type to one of A,CNAME,HINFO,MB,MG,MINFO,MR,MX 
>server NAME     - set default server to NAME, using current default server 
>lserver NAME    - set default server to NAME, using initial server 
>finger [NAME]   - finger the optional NAME 
>root            - set current default server to the root 
>ls NAME [> FILE]- list the domain NAME, with output optionally going to FILE 
>view FILE       - sort an 'ls' output file and view it with more 
> 
>... this is typical; there's ( of course ) more than one version of 
>nslookup, so ymmv. 
> 
>... usual usage is to type in the name of a host, so: 
> 
>> heaven.com 
> 
>Non-authoritative answer: 
>Name:    heaven.com 
>Address:  198.182.200.1 
> 
>... To track down email, try 
> 
>> set type=mx 
>> heaven.com 
> 
>Non-authoritative answer: 
>heaven.com      preference = 0, mail exchanger = bugs.heaven.com 
>Authoritative answers can be found from: 
>CHEX.heaven.com inet address = 206.17.180.2 
>NOC.CERF.NET    inet address = 192.153.156.22 
> 
>... Here's an undocumented feature: 
> 
>> set type=soa 
>> heaven.com 
> 
>Non-authoritative answer: 
>heaven.com      origin = chex.heaven.com 
>    mail addr = root.chex.heaven.com 
>    serial=-1436074485, refresh=10800, retry=1800, expire=604800, min=86400 
>Authoritative answers can be found from: 
>CHEX.heaven.com inet address = 206.17.180.2 
>NOC.CERF.NET    inet address = 192.153.156.22 
> 
> 
>... that mail addr = root.chex.heaven.com means that the techie 
>responsible for the heaven.com domain can be reached via 
>root@chex.heaven.com

Subject: Happy Hacker: (fwd) Question on net vandalism

>From: George Bonser <grep@cris.com> 
> 
> 
>Well the trouble is that if you put a multiuser system on the net, you 
>are responsible for security. If you EVER go into IRC expect dozens of 
>attempts to break into your system. When I go into IRC, I make it 
>impossible for ANYONE else to log into my system or connect via FTP. 
> 
>I even shut sendmail off. 
> 
> 
>George Bonser -- grep@cris.com 
>A government big enough to give you everything you want is also big enough 
>to take everything you have. --G.R. Ford, President, USA (and some others) 
>

From: "Carolyn P. Meinel" <cmeinel@techbroker.com> 
Subject: Happy Hacker: Sysadmin Magic 
From: Dale Amon <amon@galileo.gpl.com>

>---- 
> [heaven.com] 
> finger: heaven.com: Connection timed out 
> 
>There are two possible reasons for this. One is that the systems 
>adminsitrator for heaven.com has disabled the finger port. The other is that 
>heaven.com is inactive. It could be on a host computer that is turned off, 
>or maybe just an orphan. 
> 
>----- 
> 
>Comment: If it is a real domain, it may also be that there are many 
> 
>  machines and possible even subdomains. If special daemons 
>  have not been set up, or certain special measures you 
>  won't see the person. Now many universities will handle this, 
>  but many times they don't or it is haphazard. For example, 
>  I have an account on the following host with the music 
> 
>  department at Queens University Belfast: 
> 
>  finger amon@mickey.music.qub.ac.uk 
>  [mickey] 
>  Login name: amon                        In real life: Dale Amon 
>  Directory: /Net/walt/musicstore/Users/amon      Shell: /bin/csh 
>  Never logged in. 
>  No Plan. 
> 
>  I set up the DNS so that the main server answers at the 
> 
>  department level domain; however I did not take time to install 
>  a daemon that would monitor all the systems, and besides which 
>  the account that I fingered is not a network account known to 
>  the central server, thus there is an answer of sorts, but a 
> 
>  blank one. 
> 
>  finger amon@music.qub.ac.uk 
>  [music.qub.ac.uk] 
> 
>  Now if I go yet one more level up, I find that the university 
> 
>  level has not even bothered to alias that level to an IP at 
> 
>  all: 
> 
>  finger amon@qub.ac.uk 
>  unknown host: qub.ac.uk 
> 
>  But if we go to a more sophisticated domain, ie CMU, we find 
>  an entirely different story. At the host level it immediately 
> 
>  finds my plan file: 
> 
>  finger amon@h.cs.cmu.edu 
>  [H.GP.CS.CMU.EDU] 
>  Login name: amon                        In real life: Dale Amon 
>  Directory: /usrh1/amon                  Shell: /usr/cs/bin/csh 
>  Last login Tue Aug 13 12:06 on ttyv8 from galileo.gpl.net 
>  Mail came on Tue Aug 13 00:03, last read on Fri Nov 17 1995 
>  Plan: 
> 
>  At the department (actually school) level, there are two people 
>  with accounts on machines within computer science: 
> 
>  finger amon@cs.cmu.edu 
> 
>  [cs.cmu.edu] 
>  'amon' is one of 2 ambiguous names and could be: 
>  Dale Amon (amon+) 
>  Cristina Amon (camon) 
> 
>  At the university level it finds that there are two choices, 
> 
>  and even knows which departments they are in: 
> 
> 
>  finger amon@cmu.edu 
> 
>  [cmu.edu] 
>  2 users: 
>  Dale Amon            amon+@h.gp.cs.cmu.edu 
>  Cristina Amon        camon+@CMU.EDU Mechanical Engineering 
> 
> There is much more you can find from a finger, depending on how open 
> the location is and whether they run the local host versions only, or 
> have lan-wide service. For example, I can see whether any old friends 
> 
> in the department are in: 
> 
> finger @h.cs.cmu.edu 
> 
>[H.GP.CS.CMU.EDU] 
>Login       Name              TTY Idle    When            Where 
>bbernt   Benno Bernt          v0 1:24 Tue 05:27  via BBERNT.PC.CS.CMU.EDU 
>as       Allen Stoltzfus      v1    9 Tue 09:10  via STOLTZ.ADM.CS.CMU.EDU 
>ssingh   Sanjiv Singh         v4   13 Tue 08:25  via CAYENNE.FRC.RI.CMU.EDU 
>kem      Kenneth Mohnkern     v5   47 Tue 09:29  via GRAPHICSDELI.SP.CS.CMU.EDU 
>garlan   David Garlan         v6   44 Tue 09:38  via GELA.ABLE.CS.CMU.EDU 
>cdamon   Craig Arthur Damon   v7   38 Tue 10:13  via GS192.SP.CS.CMU.EDU 
>zackb    Zack Butler          v8   12 Tue 10:42  via A-HA.IUS.CS.CMU.EDU 
>crt      Roy Taylor           v9   31 Tue 10:01  via DRAKON.RESDOC.CS.CMU.EDU 
>cdamon   Craig Arthur Damon   va   44 Tue 10:03  via 
>PINK-FLOYD.COMPOSE.CS.CMU.EDU 
>dhz      Deborah H Zalewski   vb   33 Tue 08:23  via PEPPER.ADM.RI.CMU.EDU 
>me       Michael Erdmann      ve  18: Mon 14:32  via PERSEUS.TASKS.CS.CMU.EDU 
> 
> From which I see five people I know from 7 or so years ago are logged 
> into the h vax from their own office workstations. 
> 
> This can be useful if, say, I needed to open a talk session direct with 
> a compatriot on their private machine. 
> 
>----------- 
>Whoa! GNN.com is owned by America Online. Now America Online, like 
>Compuserve, is a computer network of its own that has gateways into the 
>Internet. So it isn't real likely that heaven.com would be routing email 
>through AOL, is it? It would be almost like finding a header that claims its 
>email was routed through the wide area network of some Fortune 500 
>corporation. So this gives yet more evidence that the first link in the 
>header, heaven.com, ws forged. 
>----------- 
> 
>In this case, probably true. I don't think that AOL does private domains or 
> 
>virtual popmail servers. Many ISP's do though. An address like: 
> 
>  bump.gpl.net 
> 
>will be a server for many machines, even with very different domain names. 
>The issues get complicated really fast - that particular host machine on 
>our netowrk has about 45 ip addresses and perhaps 50 different host names 
>in about 25-30 different domains! 
> 
>Often this gives you another route though - if you find the IP address, you 
>can *ALSO* track that back to the owner of the block of addresses. 
> 
>----- 
>Sounds logical, huh? Ah, but let's not jump to conclusions. This is just a 
>hypothesis and it may be wrong. So let's check out the remaining link in 
>this header: 
>----- 
> 
>Sound advice. Everything you've done appears correct, it just requires 
>caution because to every rule there is a perverse host site. 
> 
> 
>Also, I find by using a 
> 
> netstat -a 
>after doing the finger to phreak that: 
> 
>tcp        0      0  galileo.finger         albert.gnu.ai.mi.4076  SYN_RCVD 
>tcp        0      0  galileo.3138           pc.ppp.ablecom.n.finge TIME_WAIT 
> 
>Given who they are, one wonders if there is more to the finger than the 
> 
>picture. For example, certain government sites will immediately check you 
>out. And anyone running tcpd (tcp wrapper) can set up the configs to 
> 
>automatically finger a site that is unauthorized, and then leave a report in 
>the logs. 
> 
>Hmmm - maybe I shouldn't tell you so  much administrator magic ;-) 
> 
> 
>

From: "Carolyn P. Meinel" <cmeinel@techbroker.com> 
Subject: Happy Hacker: Netcom Spammer Hall of Shame 
From: Netcom Abuse Department <abuse@netcom.com> 
Reply-To: <abuse@netcom.com> 
Subject: Thank you for your report

Thank you for your report.  We have informed this user of our policies, 
and have taken appropriate action, up to, and including cancellation of 
the account, depending on the particular incident.   If they continue 
to break Netcom policies we will take further action.

The following issues have been dealt with: 
 santigo@ix.netcom.com 
 date-net@ix.netcom.com 
 jhatem@ix.netcom.com 
 kkooim@ix.netcom.com 
 duffster@ix.netcom.com 
 spilamus@ix.netcom.com 
 slatham@ix.netcom.com 
 jwalker5@ix.netcom.com 
 binary@ix.netcom.com 
 clau@ix.netcom.com 
 frugal@ix.netcom.com 
 magnets@ix.netcom.com 
 sliston@ix.netcom.com 
 aessedai@ix.netcom.com 
 ajb1968@ix.netcom.com 
 readme@readme.net 
 captainx@ix.netcom.com 
 carrielf@ix.netcom.com 
 charlene@ix.netcom.com 
 fonedude@ix.netcom.com 
 nickshnn@netcom.com 
 prospnet@ix.netcom.com 
 alluvial@ix.netcom.com 
 hiwaygo@ix.netcom.com 
 falcon47@ix.netcom.com 
 iggyboo@ix.netcom.com 
 joyful3@ix.netcom.com 
 kncd@ix.netcom.com 
 mailing1@ix.netcom.com 
 niterain@ix.netcom.com 
 mattyjo@ix.netcom.com 
 noon@ix.netcom.com 
 rmerch@ix.netcom.com 
 rthomas3@ix.netcom.com 
 rvaldes1@ix.netcom.com 
 sia1@ix.netcom.com 
 thy@ix.netcom.com 
 vhs1@ix.netcom.com

Sorry for the length of the list.

Spencer 
Abuse Investigator 
_______________________________________________________________________ 
NETCOM Online Communication Services                       Abuse Issues 
24-hour Support Line: 408-983-5970                     abuse@netcom.com

Fri Aug 30 07:39:37 1996 
From: "Carolyn P. Meinel" <cmeinel@techbroker.com> 
Subject: Happy Hacker: Linux/Unix learning

>From: "Sin DeKated" <sindekated@sincom.com>

>On a good note, the Linux/UNIX learning is going very well, and I thank you 
>for advising me to install the Linux system!  I have Win95, DOS 6.22 & 
>Linux running flawlessly on my system, and I love it!  :-) 
> 
>Take care and thanks again! 
> 
>Sin 
>------- 
>Profanity is the one language all programmers know best. 
>                      -Murphy's Law of programming 
> 
