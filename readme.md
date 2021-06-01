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

## Supported Sandbox-mode Configuration
A variety of configuration from the (Windows) FPSci application is supported in this application, including:

* Rendering
    * Frame rate
    * Frame delay
    * Use late warp?
    * Field of View (horizontal)
    * Show the (score) banner?
    * Click-to-photon monitoring
* Audio
    * Play fire audio?
    * Play target explision audio?
    * Add audio latency
* Scene - Generated, so different from FPSci
    * Overall width/depth
    * Sky color/use of a cubemap-based skybox (requries local hosting)
    * Floor color
    * Fog color and distances
    * Wall height and color (for edge of the scene)
    * Boxes (geometry within the scene)
        * Count of boxes
        * Box geometry (width, depth, height range)
        * Distance from boxes to player spawn postion
        * Base color
        * Color scale range (randomized within for individual boxes)
    * Regenerate a new (random) scene based on parameters above
* Player
    * Mouse sensitivity (arbitrary units)
    * Height
    * Speed
    * Jump Height
    * Collision detection (within the scene)
    * Reticle
        * Color
        * Base size (extents)
        * Gap size
        * Expanded scale (after a shot)
        * Shrink time (after a shot)
* Target
    * Count (simultaneous targets)
    * Color (full/min health are interpolated between)
    * Size (min/max randomized)
    * Movement parameters (randomized)
        * Min/max speed
        * Min/max change time
    * Spawn position (randomized in range)
        * Azimuth/Elevation range (relative to most recent player view)
        * Min/max distance
    * Particles (drawn on hit)
        * Size
        * Count to spawn on hit
        * Count to spawn on destroy
    * Reference target
        * Size
        * Distance
* Weapon
    * Automatic fire
    * Fire period 
    * Damage/s (multiply by fire period to get damage/shot)
    * Scope controls
        * Has scope?
        * Toggle vs hold for scope
        * Field of view when scoped

