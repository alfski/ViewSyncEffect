#ViewSyncEffect.js 

Based on StereoEffect.js from vr.chromeexperiments.com.

Change websocket server from "ws://192.168.0.233:3000/relay" to the URI of your websocket relay/echo service.

Copy lglions.html and lgpompei.html into the /examples/ folder in the potree distribution


How to call the apps...

```
Master http://YOURWEBSERVER/lglion.html
Slaves http://YOURWEBSERVER/lglion.html?slave&fov=30&yaw=33

Master http://YOURWEBSERVER/lgpompei.html
Slaves http://YOURWEBSERVER/lgpompei.html?slave&fov=25&yaw=-29
```

"slave" enables camera sync.
"fov" to set the camera horizontal field of view. Can also available on master.
"yaw" set the slave camera yawOffset, in degrees.
