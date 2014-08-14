#ViewSyncEffect.js 

_Note: this README is a work in progress_

Based on StereoEffect.js from [vr.chomeexperiements.com](http://vr.chromeexperiments.com/).

Shares the camera position and quaternion to a websocket relayer.

Wraps the camera in the ThreeJS app, with a camera that is setable from a websocket and with configurable fov and yaw offset.

```
<script src="ViewSyncEffect.js"></script>
...
var viewSyncEffect = new THREE.ViewSyncEffect( renderer );
viewSyncEffect.setSize( window.innerWidth, window.innerHeight );
...
viewSyncEffect.render( scene, camera );
```

FYI when reading the examples, I tend to comment with `// Alf` the major changes.

##How to use/implement these demo's

Place `ViewSyncEffect.js`, `lglion.html` and `lgpompei.html` in the /examples/ folder of an existing potree distribution. See [potree.org](http://potree.org/)

Change websocket server in `ViewSyncEffect.js` from `ws://192.168.0.233:3000/relay` to the URI of your websocket relay/echo service.
Any simple websocket echo server will do the job. I have one in Perl. 'coz I'm oldskool.

##How to launch the app examples

```
Master http://YOURWEBSERVER/lglion.html
Slaves http://YOURWEBSERVER/lglion.html?slave&fov=30&yaw=33

Master http://YOURWEBSERVER/lgpompei.html
Slaves http://YOURWEBSERVER/lgpompei.html?slave&fov=25&yaw=-29
```

##URL Parameters

`?slave` configures app to receive camera sync. Otherwise it is a master and will send its camera to the websocket relay.

`?fov=DEGREES` set the camera horizontal field of view. This parameter can be used on master or slave.

`?yaw=DEGREES` set the slave camera yawOffset. Also works on master, but not sure why you would want to! Currently, if you do this on a master, the un-offset view is what wll be shared.

##Issues, ToDo's & Notes

* issue: This only seems to work is there's a single scene to render. To get the sky box I had to merge it with the point cloud scene. How to deal with multiple scenes or post-processing.

* todo: convert more of the vr.chromeexperiments.com demos to Liquid Galaxy. can we do this on-demand?

* todo: possibly add pitch and roll offseting. Mainly for 'ViewSync' completeness.

* todo: I think there's cleanups around when/where the slave and master camera needs to be set. It may be doing more work than it needs to.

* todo: make a smarter relayer. eg. one that resends last sent camera pov on slave connect.

* todo: look at websocket-enabling "dat.gui.js" (control GUI)

* todo: could maybe also look at OrbitControls.

* todo: we need a SpaceNavigator/GamePadAPI camera control for ThreeJS/webgl. Student project?

* todo: convert to binary websockets and ditch the JSON stringify and parse steps.

* todo: perhaps limit the number of signficant figures in shared camera, not so much a problem if JSON is in binary.

* todo: check qryArgs parse as numbers, check range, fallback to safe values.

* todo: finish up and share Go based websocket relayer.

* todo: really need to be using a broadcast messaging system rather than client-server. Maybe a Chrome socket plugin or WebRTC data channel?

* note: potree could benefit from a LOD setting based on a preferred fps. To help smooth jitter between slaves.

* note: for lgpompei.html I disabled the skybox so it renders against a simple black background. I think it looks better.

## Changelog

* 2013.08.13 first public release outside of Wonderama Lab
