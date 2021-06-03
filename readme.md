# 2021 SIGGRAPH Emerging Technologies Latency and Late Warp Demo
This is a simple interactive experience intended to demonstrate the effects of changes in system latency on task performance in first-person targeting tasks, and possible corrections using late warp techniques.

## Experience
The user begins by opening/reloading the page which automatically starts the "experiment" mode, wherein an initial training period, followed by 3 different latency conditions are provided. Each condition consists of a series of trials beginning with a red reference target (used to reset aim direction).

Following completeing the three measurement conditions the application provides a brief summary display that compares:
* The average (per target) completion time in each condition
* The overall accuracy in each condition
* The latency introduced by each condition
* The difference of task completion time/accuracy caused by the condition

After this the application enters a *sandbox* mode in which the user can control arbitrary parameters including frame rate and latency. In this mode the banner shown at the top of the screen can be used to capture average target time/accuracy metrics.

### Latency Conditions
We provide 3 latency conditions in our experiment:

1. A ground truth condition that adds no (0) frames of latency between user input and output
2. A delayed condition that adds ~80 ms of latency to the rendered view
3. A condition that adds ~80 ms of latency to rendering that it then attempts to correct for with a late warp

## Running the Application
The application works in a browser run from one of two modes:

* File hosted mode: Works when not using assets with the application (i.e. no local files/images required)
* Hosted through `localhost` (or another web-hosting option) 

Since our current demo does not rely on any hosted assets it can be run in either mode, but we suggest file hosted as it is simpler.

To open the application in file hosted mode simply open the `Late Warp Web Demo.html` page in a browser of your choice (we suggest Chrome). Here all features will work *except* those that require local file contents.

After hosting the directory through `localhost` the application can be accessed by visiting `http://localhost:8000/index.html`.

## Supported Configuration
A variety of configuration from the (Windows) FPSci application is supported in this application. The application can be configured either through loading a JSON file from disk, or by using URL parameters.

Currently supported configuration is provided as a nested list below. The format is: [Parameter Name]: [`URL Parameter Name`] (`type`) = [Default Value].

Typically JSON parameter names are _very_ similar to URL parameter names, but often with less verbosity as they are inherently nested in the configuration dictionary.

* Rendering
    * Set frame rate?: `setFPS` (`Boolean`) = `False`
    * Frame rate: `frameRate` (`Number`) = `60`
    * Frame delay: `frameDelay` (`Integer`) = `0`
    * Late warp correction?: `latewarp` (`Boolean`) = `False`
    * Field of View (horizontal): `hFoV` (`Number`) = `103`
    * Show rendering statistics?: `showStats` (`Boolean`) = `False`
    * Show score banner?: `showBanner` (`Boolean`) = `True`
    * Fullscreen mode?: `fullscreen` (`Boolean`) = `True`
    * Click-to-photon monitoring
        * Show click to photon-monitor?: `showC2P` (`Boolean`) = `False`
        * Certical position: `c2pVertPos` (`Boolean`) = `0.5`
        * Output mode: `c2pMode` (`"immediate"` or `"delayed"`) = `"immediate"`
        * Width of area: `c2pWidth` (`Number` 0-1) = `0.2`
        * Height of area: `c2pHeight` (`Number` 0-1) = `0.2`
        * Mouse up color: `c2pUpColor` (`Color`) = `#222222`
        * Mouse down color: `c2pDownColor` (`Color`) = `#AAAAAA`
* Audio
    * Play fire audio?: `playFireSound` (`Boolean`) = `True`
    * Play target explision audio?: `playExplodeSound` (`Boolean`) = `True`
    * Added audio latency: `AudioDelayMs` (`Number`) = `0`
* Scene - Generated, so different from FPSci
    * Sky color (no cubemap): `skyColor` (`Color`) = `#c6defa`
    * Use a cubemap-based skybox?: `cubemapSky` (`Boolean`) = `False`
    * Scene width: `sceneWidth` (`Number`) = `1000`
    * Scene depth: `sceneDepth` (`Number`) = `1000`
    * Floor color: `floorColor` (`Color`) = `#756b5a`
    * Fog 
        * Color: `fogColor` (`Color`) = `#ffffff`
        * Near distance: `fogNear` (`Number`) = `0`
        * Far distance: `fogFar` = `1000`
    * Walls (scene bounds)
        * Color: `wallColor` (`Color`) = `#2a2713`
        * Height: `wallHeight` (`Number`) = `80`
    * Boxes (geometry within the scene)
        * Count of boxes: `boxCount` (`Integer`) = `200`
        * Min height (uniform random in range): `boxMinHeight` (`Number`) = `20`
        * Max height (uniform random in range): `boxMaxHeight` (`Number`) = `100`
        * Width (same for all): `boxWidth` (`Number`) = `20`
        * Depth (same for all): `boxDepth` (`Number`) = `20`
        * Distance from boxes to player spawn postion: `boxRange` (`Number`) = `500`
        * Minimum distance from box to player (clearing size): `boxMinDistance` (`Number`) = `80`
        * Base color (scaled): `boxColor` (`Color`) = `#ffffff`
        * Color scale range (randomized range): `boxColorScale` (`Number` 0-1) = `0.5`
    * _Regenerate a new (random) scene based on parameters above using a button or by reloading_
* Player
    * Movement Speed: `playerSpeed` (`Number`) = `500`
    * Mouse sensitivity (arbitrary units): `mouseSensitivity` (`Number`) = `0.2`
    * Height: `playerHeight` (`Number`) = `5`
    * Jump Height: `playerJumpHeight` (`Number`) = `250`
    * Collision detection (within the scene): `playerCollision` (`Boolean`) = `True`
    * Collision distance: `playerCollisionDistance` (`Number`) = `3`
    * Reticle (aim direction indicator)
        * Color: `reticleColor` (`Color`) = `#000000`
        * Base size (extents): `reticleSize` (`Number`) = `0.03`
        * Gap size: `reticleGap` (`Number`) = `0.01`
        * Expanded scale (after a shot): `reticleExpandScale` (`Number` ratio) = `2`
        * Shrink time (after a shot): `reticleShrinkTime` (`Number` seconds) = `0.3`
* Target
    * Count (simultaneous targets): `targetCount` (`Integer`) = `1`
    * Min size (uniform random in range): `targetMinSize` (`Number`) = `0.5`
    * Max size (uniform random in range): `targetMaxSize` (`Number`) = `3`
    * Movement parameters (uniformly randomized in range)
        * Min speed (along a line): `targetMinSpeed` (`Number`) = `5`
        * Max speed (along a line): `targetMaxSpeed` (`Number`) = `15`
        * Min motion change time (new direction selection interval): `targetMinChangeTime` (`Number`) = `1`
        * Max motion change time (new direction selection interval): `targetMaxChangeTime` (`Number`) = `3`
    * Color (full/min health are interpolated between)
        * Full/max health color: `targetMaxHealthColor` (`Color`) = `#00ff00`
        * Min/no health color: `targetMinHealthColor` (`Color`) = `#ff0000`
    * Spawn position (uniformly randomized in range)
        * Min spawn distance: `targetMinSpawnDistance` (`Number`): `20`
        * Max spawn distance: `targetMaxSpawnDistance` (`Number`): `30`
        * Max azimuth spawn angle (± relative to most recent player view): `targetSpawnMaxAzim` (`Number` degrees) = `35`
        * Min azimuth spawn angle (± relative to most recent player view): `targetSpawnMinAzim` (`Number` degrees) = `20`
        * Max elevation spawn angle (± relative to most recent player view): `targetSpawnMaxElev` (`Number` degrees) = `10`
        * Min elevation spawn angle (± relative to most recent player view): `targetSpawnMinElev` (`Number` degrees) = `3`
    * Reference target (red target used to reset aim direction on reload/start of trial)
        * Size: `refTargetSize` (`Number`) = `1`
        * Distance: `refTargetDistance` (`Number`) = `30`
    * Particles (drawn on hit/destory events)
        * Size: `particleSize` (`Number`): `0.4`
        * Count to spawn on hit: `hitParticleCount` (`Integer`) = `25`
        * Count to spawn on destroy: `destroyParticleCount` (`Integer`) = `1000`
* Weapon
    * Automatic fire (hold left mouse to fire): `weaponAuto` (`Boolean`) = `False`
    * Fire period (rate of fire): `weaponFirePeriod` (`Number`) = `0.1` (10 shots per s ==> 600 rounds per minute)
    * Damage/s (multiply by fire period to get damage/shot): `weaponDPS` (`Number`) = `10` (1-hit destroy as all targets have 1 life)
    * Fire spread angle (symmetric): `weaponFireSpread` (`Number` degrees) = `0.5`
    * Scope controls
        * Has scope?: `weaponScope` (`Boolean`) = `False`
        * Toggle vs hold for scope: `weaponScopeToggle` (`Boolean`) = `True` (toggled scope by default)
        * Field of view when scoped: `weaponScopeFoV` (`Number`) = `50`
