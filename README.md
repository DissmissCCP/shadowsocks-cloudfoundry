shadowsocks-cloudfoundry
===========

forked from shadowsocks-dotcloud

shadowsocks-cloudfoundry is a lightweight tunnel proxy which can help you get through
 firewalls. It is a port of [shadowsocks](https://github.com/clowwindy/shadowsocks), but
 through a different protocol.


Notice that the protocol is INCOMPATIBLE with the origin shadowsocks.

usage
-----------

Sign up for [IBM Bluemix](https://console.ng.bluemix.net/).

Creat a new cloudfoundry node.js app,don't close the instruction window,there will be useful.

Follow the instructions to install [cloudfoundry-cli](https://github.com/cloudfoundry/cli).

Put the code somewhere, for example shadowsocks-cloudfoundry/. Edit `config.json`, change the following values:

    server          your server hostname, for example, YOURCFAPP.mybluemix.net
    local_port      local port
    password        a password used to encrypt transfer
    timeout         in seconds
    method          encryption method, null by default, or use "rc4"

Edit `manifest.yml`, change the following values:

    memory          change 128M to 256M,if you want larger RAM
    name            your cloudfoundry app name,for example,yourcfapp
    host            your cloudfoundry app name,for example,yourcfapp

Push the code to Bluemix cloudfoundry,change 'youremailaddress','yourorgname','yourspacename','yourcfapp' to exactly yours.

    cf api https://api.ng.bluemix.net
    cf login -u youremailaddress -o yourorgname -s yourspacename
    cf push yourcfapp

Waiting until uploading and compling complete,there will be shown your app is running.

[Node.js install instructions](https://github.com/nodesource/distributions).

Open terminal , run `node local.js`.

Change proxy settings of your browser into

    SOCKS5 127.0.0.1:local_port


troubleshooting
----------------

If there is something wrong, you can check the logs.

usage for cloudnode
-----------

Delete the manifest.yml,this file is useless for cloudnode.

Open server.js change port 8080 to cloudno.de signed port for you,you can't use any listing port as you want.

git add and git push to your cloudnode app.
