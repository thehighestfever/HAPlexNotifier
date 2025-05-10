Steps for setting up media player notifications via HTML5

This automation triggers when the content ID attribute of your chosen media player entity changes.  It generates a new JPG from the entity_picture every time it triggers with the filename generated from the content ID.  
It would be easier to simply call the image "albumart.jpg" and overwrite the existing image every time.  But becuase Chrome caches the notification images we have to change the filename each time a notification is generated or 
the image will stay the same until your cache is cleared.  The shell command is inlcuded as housekeeping to prevent a single folder from filling with thousands of images in a very short period of time.  

- Create a folder within your /config/wwww/ folder to store the album art image for each track.  This folder will be emptied each time the track changes.
- 
- Add the included shell command to your configuration.yaml and point it at the folder you made to store your album art image.  Save and reboot HA.
- 
- Add the Generic Camera integration, or add a device to it if you already have the integration.  Create a camera, using the Still Image option and the local URL of album art folder and file name.
- The Generic Camera requires a URL and not just a local directory.  You can work around this by using your local HA address and adding the state_attr and image attribute of your chosen media player, in this case:
- http://homeassistant.local:8123{{ state_attr('media_player.plex_plexamp_android', 'entity_picture') }}

- Create your automation using the included yaml code.  Modify URLs and folder locations as needed.
