After so much theory, it seems like it's time to look at how we can apply these principles in the real world.

The following is based the summary of an issue from just a few weeks ago.  It's heavily edited and anonymized, and I've tried to add the **Risk-First** vocabulary along the way, but otherwise, it's real.

Some background:  **Synergy** is an online service with an app-store, and **Eve** and **Bob** are developers working for **Large Corporation LTD**, which wants to have an application accepted into Synergy's app-store.  

Synergy's release means that the app-store refresh will happen in a few weeks, so this is something of a hard deadline: if we miss it, the next release will be four months away.

## A Risk Conversation

**Eve**:  We've got a problem with the Synergy security review.  

**Bob**:  Tell me.

**Eve**:  Well, you know Synergy did their review and asked us to upgrade our Web Server to only allow TLS version 1.1 and greater?  

**Bob**:  Yes, I remember:   We discussed it as a team and thought the simplest thing would be to change the security settings on the Web Server, but we all felt it was pretty risky.  We decided that in order to flush out [Hidden Risk](Attendant-Risk), we'd upgrade our entire production site to use it _now_, rather than wait for the app launch.

**Eve**:  Right, and it _did_ flush out [Hidden Risk](Attendant-Risk): some people using Windows 7, downloading Excel spreadsheets on the site, couldn't download them:  for some reason, that combination didn't support anything greater than TLS version 1.0.  So, we had to back it out.

**Bob**:  Ok, well I guess it's good we found out _now_.  It would have been a disaster to discover this after the go-live.

**Eve**:  Yes.  So, what's our next-best action to mitigate this?  

**Bob**:  Well, we could go back to Synergy and ask them for a reprieve, but I think it'd be better to mitigate this risk now if we can... they'll definitely want it changed at some point.

**Eve**:  How about we run two web-servers?  One for the existing content, and one for our new Synergy app?  We'd have to get a new external IP address, handle DNS setup, change the firewalls, and then deploy a new version of the Web Server software on the production boxes.

**Bob**:  This feels like there'd be a lot of [Attendant Risk](Attendant-Risk):  and all of this needs to be handled by the Networking Team, so we're picking up a lot of [Bureaucratic Risk](Bureaucratic-Risk).  I'm also worried that there are too many steps here, and we're going to discover loads of [Hidden Risks](Attendant-Risk) as we go.

**Eve**:  Well, you're correct on the first one.  But, I've done this before not that long ago for a Chinese project, so I know the process - we shouldn't run into any new [Hidden Risk](Attendant-Risk).

**Bob**:  Ok, fair enough.  But isn't there something simpler we can do?  Maybe some settings in the Web Server?

**Eve**:  Well, if we were using Apache, yes, it would be easy to do this.  But, we're using Baroque Web Server, and it _might_ support it, but the documentation isn't very clear.

**Bob**:  Ok, and upgrading it is a _big_ risk, right?  We'd have to migrate all of our [configuration](Configuration-Riks)... 

**Eve**:  Yes, let's not go there.  But if we changing the settings on Baroque, we have the [Attendant Risk](Attendant-Risk) that it's not supported by the software and we're back where we started.  Also, if we isolate the Synergy app stuff now, we can mess around with it at any point in future, which is a big win in case there are other [Hidden Risks](Attendant-Risk) with the security changes that we don't know about yet.

**Bob**:  Ok, I can see that buys us something, but time is really short and we have holidays coming up.  

**Eve**:  Yes. How about for now, we go with the isolated server, and review next week?  If it's working out, then great, we continue with it.  Otherwise, if we're not making progress next week, then it'll be because our isolation solution is meeting more risk than we originally thought.   We can try the settings change in that case.

**Bob**:  Fair enough, it sounds like we're managing the risk properly, and because we can hand off a lot of this to the Networking Team, we can get on with mitigating our biggest risk on the project, the authentication problem, in the meantime.

**Eve**:  Right.  I'll check in with the Networking Team each day and make sure it doesn't get forgotten.

## Aftermath

Hopefully, this type of conversation will feel familiar.  It should.  There's nothing ground-breaking at all in what we've covered so far; it's more-or-less just Risk Management theory.  

If you can now apply it in conversation, like we did above, then that's one extra tool you have for delivering software.  

When we work on a team, though, we want to pick up actions and just _get stuff done_ without having to debate the finer points of each risk over and over again.  

This is where process comes in.   It's time to look at some [Methodologies](Methodologies).



 