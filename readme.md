# Javscript FPSci
This documentation supports the "FPSci in a broswer" approach developed in this project.

## Current Support
Currently the application is not intended to support full experiments in the style of FPSci. Instead it focuses on programmable user experience for "feel"-based experiences. This means that many controls that would normally be hidden in the FPSci app are available in app here.

In addition no output files are current produced. This could easily be changed in the future.

## Running the Application
The application works in a browser run from one of two modes:

* File hosted mode: Works when not using assets with the application (i.e. no local files/images requires)
* Hosted from `localhost` 

### File Hosted
To open the application in file hosted mode simply open the `index.html` page in a browser of your choice. Here all features will work *except* those that require local file contents.

### Running with Local Host
To run with local host the top-level directory for this project needs to be hosted through `localhost`. This can be done with Python using the `python -m http.server` command and a script ([`open_localhost.bat`](open_localhost.bat)) is provided to do exactly this (plus open the correct URL).

After hosting the directory through `localhost` the application can be accessed by visiting `http://localhost:8000/index.html`.

## Supported Configuration
A variety of configuration from the (Windows) FPSci application is supported in this application, including:

* Rendering
    * Frame rate
    * Frame delay
    * Late warp correction
    * Field of View (horizontal)
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