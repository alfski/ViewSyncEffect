#ViewSyncEffect.js 

Based on StereoEffect.js from vr.chromeexperiments.com.

Shares the camera position and quaternion to a websocket relayer.

Wraps the camera in the ThreeJS app, with a camera that is setable from a websocket and with particular fov and yaw offset.

`<script src="ViewSyncEffect.js"></script>`

##How to use/implement these demo's

Place ViewSyncEffect.js, lglion.html and lgpompei.html into the /examples/ folder in the potree distribution

Change websocket server from "ws://192.168.0.233:3000/relay" to the URI of your websocket relay/echo service.
Any simple websocket echo server will do the job. I have one in Perl... just 'coz I'm oldskool.

##How to launch the apps

```
Master http://YOURWEBSERVER/lglion.html
Slaves http://YOURWEBSERVER/lglion.html?slave&fov=30&yaw=33

Master http://YOURWEBSERVER/lgpompei.html
Slaves http://YOURWEBSERVER/lgpompei.html?slave&fov=25&yaw=-29
```

##Parameters

"slave" enables camera sync.

"fov" to set the camera horizontal field of view, in degrees. This parameter can also be used to set the master fov for display purposes.

"yaw" set the slave camera yawOffset, in degrees.

##Issues & To Do's

* possibly add pitch and roll offseting, just for 'ViewSync' completeness.

* I think there's cleanups to when the camera needs to be set.

* smarter relayer, that resends current camera pov.

* look at websocket-enabling "dat.gui.js"

