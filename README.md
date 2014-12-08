# SSBui - The first client for the secure-scuttlebutt network

To setup:

```
npm install -g ssbui
ssbui
```

Then open `localhost:2000` in your browser and get started!

## Hosting a Public Relay

To give good uptime to the ssb network, bot users run as "public relays." They follow users who want to be hosted; friends of friends contact the relay bot to get each others' messages from it.

To setup a public relay host, ssh into your server and run the following commands:

```
npm install -g ssbui
ssbui server --hostname <your_domain>   # do this in a screen which you can detach
ssbui add --type profile --nickname <relay_nickname>
```

For instance:

```
ssbui server --hostname goodpeople.com
ssbui add --type profile --nickname goodpeople.com
```

To host somebody on the relay, you have the relay follow the target user. You can do that with this command:

```
ssbui add --type follows --rel follows --feed <target_id>
```

For instance:

```
ssbui add --type follows --rel follows --feed r+MiCfhoSQm10BfneXkmtG/H5sioWZW0yrPOkXr5i94=.blake2s
```

## Adding a Public Relay

To add a public relay to your local device (eg one you hosted) run the following command on your local computer (with ssbui running):

```
ssbui add --type pub --address <hostname>
```

For instance:

```
ssbui add --type pub --address goodpeople.com
```