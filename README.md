#ViewSyncEffect.js 

Based on StereoEffect.js from vr.chromeexperiments.com.

Change websocket server from "ws://192.168.0.233:3000/relay" to the URI of your websocket relay/echo service.

Copy lglions.html and lgpompei.html into the /examples/ folder in the potree distribution


How to call the apps...

'''
Master -- /lglions.html
Slaves -- /lglions.html?slave&fov=30&yaw=33

Master -- /lgpompei.html
Slaves -- /lgpompei.html?slave&fov=25&yaw=-29
'''
