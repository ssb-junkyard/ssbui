# SSBui - ssb install package for desktop users

To setup:

```
npm install -g ssbui
ssbui
```

If this gives you a permissions error, [use the method here (preferred)](http://stackoverflow.com/questions/19352976/npm-modules-wont-install-globally-without-sudo) or install and run using sudo.

Then open `localhost:2000` in your browser and get started!

## Hosting a Public Relay

To give good uptime to the ssb network, bot users run as "public relays." They follow users who want to be hosted; friends of friends contact the relay bot to get each others' messages from it.

To setup a public relay host, ssh into your server and run the following commands:

```
npm install -g ssbui
ssbui server --hostname <your_domain>   # do this in a screen which you can detach
ssbui publish --type profile --nickname <relay_nickname>
```

For instance:

```
ssbui server --hostname goodpeople.com
ssbui publish --type profile --nickname goodpeople.com
```

To host somebody on the relay, you have the relay follow the target user. You can do that with this command:

```
ssbui publish --type follows --rel follows --feed <target_id>
```

For instance:

```
ssbui publish --type follows --rel follows --feed r+MiCfhoSQm10BfneXkmtG/H5sioWZW0yrPOkXr5i94=.blake2s
```

## Generating an Invite Code

Invite codes allow public relays to distribute secrets that allow a set number of local clients to automatically follow and be followed by the public relay.

To generate an invite code, run the following command on your public relay (with ssbui running):

```
ssbui invite.create <number of times invite code can be consumed>
```

For instance:

```
ssbui invite.create 10
```

To consume the invite code, copy and paste the output of the above `invite.create` command into the "Add contact" dialog of a local ssbui interface.

## Adding a Public Relay

To add a public relay to your local device (eg one you hosted) run the following command on your local computer (with ssbui running):

```
ssbui publish --type pub --address <hostname>
```

For instance:

```
ssbui publish --type pub --address goodpeople.com
```
