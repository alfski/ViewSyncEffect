#ViewSyncEffect.js 

Based on StereoEffect.js from vr.chromeexperiments.com.

Shares the camera position and quaternion to a websocket relayer.

Wraps the camera in the ThreeJS app, with a camera that is setable from a websocket and with particular fov and yaw offset.

`<script src="ViewSyncEffect.js"></script>`

When reading the examples files I comment with "Alf" any major changes.

##How to use/implement these demo's

Place ViewSyncEffect.js, lglion.html and lgpompei.html into the /examples/ folder in the potree distribution

Change websocket server in ViewSyncEffect.js from "ws://192.168.0.233:3000/relay" to the URI of your websocket relay/echo service.
Any simple websocket echo server will do the job. I have one in Perl. 'coz I'm oldskool.

##How to launch the app examples

```
Master http://YOURWEBSERVER/lglion.html
Slaves http://YOURWEBSERVER/lglion.html?slave&fov=30&yaw=33

Master http://YOURWEBSERVER/lgpompei.html
Slaves http://YOURWEBSERVER/lgpompei.html?slave&fov=25&yaw=-29
```

##Parameters

"?slave" enables camera sync. Otherwise it is a master and will send it's camera to the websocket relay.

"?fov=DEGREES" to set the camera horizontal field of view. This parameter can also be used to set the master fov for display purposes.

"?yaw=DEGREES" set the slave camera yawOffset.

##Issues & To Do's & Notes

* issue: only seems to work is there's a single scene to render. To get the sky box I had to merge it with the point cloud scene.

* todo: possibly add pitch and roll offseting. Mainly for 'ViewSync' completeness.

* todo: I think there's cleanups around when/where the slave and master camera needs to be set. It may be doing more work than it needs to.

* todo: smarter relayer, that resends current camera pov on request from a slave start.

* todo: look at websocket-enabling "dat.gui.js"

* note: potree could benefit from a LOD setting based on a preferred fps. To help smooth jitter between slaves.

* note: in lgpompei.html I disabled the Skybox to give better visual contrast.

* todo: convert to binary websockets and ditch the JSON stringify/parse step.
