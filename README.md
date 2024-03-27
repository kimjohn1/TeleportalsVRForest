This is a custom asset package.  You will need to create a new 3D Core Unity Project using Editor version 2021.3.36f1 (newer will not work), then set the 
project up for VR by installing XR Plugin Management and XR Interaction toolkit.  Import the Starter Assets Sample from the XR Interaction Toolkit as well.

Go to Edit -> Project Settings and set up XR Plugin Management, Open XR and XR Interaction Toolkit.  You can use the Project Validation Fix All option
to speed that setup process along.

Download this custom asset by clicking on Code -> Download Zip File, and saving the download somewhere you will remember.  In the open package that you have 
set up, down at the bottom in the Project panel, click on Assets in the file tree, to get the loaded assets showing in the right side of the panel.  Right 
mouse click with the cursor in the right side of the Project panel to get a menu and then click on Import Package -> Custom Package and navigate to where you 
saved the TeleportalsVRForest custom asset.  Double click that file to get the Import dialog and click on Import.

You will need to set up Layers in the Project.  Here is how I do it: Click on Terrain in the Hierarchy panel and then in the Inspector panel click on the Layer
drop down menu.  Click on Add Layer... and add TestLayer as #3, RightEye as #6 and blank as #7.  Make sure the Layer selected for Terrain is TestLayer when 
you are done adding Layers.  Click on XR Origin in Hierarchy and verify that the Layer selection in the Inspector panel is Default.  At the bottom of the 
Inspector panel, verify that Layer Mask is set to TestLayer.

Click on the dropdown caret for XR Origin in the Hierarchy panel and verify or set the Layer selection for portalQuadL is set to blank, and the Layer selection 
for portalQuadR is set to RightEye.  Click on the dropdown caret for Camera Offset and verify or set the Layer selection for portalParentL is set to RightEye,
and portalParentR is set to blank.

You should be able to run the project and have a functional teleport capability working when you press the right controller A button.  A couple of things are 
immediately apparent:

* The view seen in the portal window as it approaches is not the destination view.  It is just a portal ring showing the view you have where you are standing, and 
when the portal ring envelops you, there is a sudden jump to the destination.  So this implementation fails to present the most important characteristic of "the
destination being brought to you", rather than "you being moved rapidly or suddenly to the destination".  We will need to fix that.
* The implementation is crude - The teleportal feature is always on, the destination is indicated by a large capsule, the portal does not stop in front of you, and
  there is no way to slew the destination view around so you can decide to complete the jump, or stay where you are.

If I change portalQuadL Layer to RightEye the left eye shows the destination view in the portal ring as it approaches, and the right eye still shows the starting
position view until the portal ring envelops the user, then jumps to the destination.  I have asked the authof of this Project to tell me how he has programmed
the different cameras with Layer selections that produce a destination view in both eyes.  I have not heard back from him in almost a week.  -KJ
