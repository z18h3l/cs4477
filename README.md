java c
CSE 386
Fall 2024
Project Ray Tracing
Notes:
● Your project must be an interactive program that responds to the keystrokes, as outlined in the keystroke document (see outline for document link).
● fullraytrace.cpp (see outline for link to source code) has been provided to you to serve as a starting point for your main driver. Its main purpose:
○ Handle the keystrokes listed in the keystroke document. You should not need to alter the function keyboard().
○ You can make other changes as needed (e.g., add/delete items from scene or pass new parameters to rytraceScene).
● A video has been provided to illustrate the behavior. of the project (see outline for video links).
● You may not use code distributed in previous semesters or code developed by other students/AI bots; you are expected to complete this project on your own (of course collaboration at the pseudo code/algorithm level is appropriate and encouraged). It is also worth noting that there are subtle differences between this semester’s code base and previous semesters. In addition, scripts will be run to detect unnatural similarities between all student submissions.
● You may not use glViewport or any other gl or glu functions. We never talked about these and you should not be using them. Of course, you may use glm functions.(77) REQUIRED FEATURES

1. (35) Lighting, shading, and shadows. The lighting/shading of your scene must include:
a. (21) One positional light and the correct implementation of the equations to render the objects with a realistic appearance.
b. (7) Shadows. Implement shadows by checking shadow feelers for each surface intersection. If the shadow feeling intersects with another surface before the shadow feeler reaches the light source, that particular light should provide only ambient contribution.
c. (7) Spotlight. The spotlight will not illuminate any intersection points that fall outside the light’s cone. If outside the cone, the light considers the intersection point as black; otherwise, the intersection point is rendered like a regular positional light. (Note: spotlights often have a different approach for rendering the interior of the cone. Our class will simply render the interior of the cone as would be done with a normal positional light.)
2. (28) Objects. Your scene must include, at a minimum, the following objects, each with their own material common properties (e.g., gold).
a. (7) Y-oriented, finite-length, cylinder with open ends. Put an untextured one of these in your scene. This must be a different size from the textured one. Backfaces must be rendered correctly.
b. (7) Y-oriented, finite-length, cylinder with closed ends. Put at least one of these in your scene. The implementing class should be named IClosedCylinderY.
c. (7) 1 triangle.
d. (3) 1 disk.
e. (1) Put at least one sphere in your scene.
f. (3) Put at least one plane in your scene.
3. (7) Textures. One Y open-ended oriented cylinder must have its sides textured with any recognizable PPM file, such as the US flag (do not use a texture such as cement or a pile of rocks. Do this by merging the texel value and illuminated value at the intersection point at 50-50 proportions. Because the texel colors are being added in directly, textured objects will appear bright even if lights are off.
4. (7) Transparency. One planar shape in your scene has been placed on a timer to alter its position. This should be transparent. The position of the transparent object is placed on a timer to illustrate that the display is correct, given its relative position to opaque objects. That is, the transparent object must move in front of and then behind opaque objects.

Transparent objects are not to be textured and are not subjected to the lighting calculations. Instead, treat it as a simple color (i.e., its ambient color). Assume that at most one transparent object will intersect the viewing ray. Lastly, the transparent object can be ignored when doing reflections.(23) ADVANCED FEATURES
Your first features is worth 14 and the second worth points 9 points
1. Reflections. Add inter-object reflections by tracing a reflection ray to the closest surface intersection for each view ray. Once generated, the reflection ray can be traced in exactly the same way as the viewing rays. The best way to accomplish this is by calling the traceIndividualRay method recursively and adding what it returns to the total color for the pixel. To do this, it is necessary to keep the recursion from being infinite. This can be accomplished by adding an additional parameter -- depth --  to the traceIndividualRay method. This parameter can be reduced by one prior to each recursive call. The recursion would stop when the value is less than or equal to zero.
2. Anti-aliasing. Because of the discrete nature of raster image representation, rendered images will include aliasing artifacts. These artifacts create a 代 写CSE 386 Fall 2024 Project Ray TracingC/C++
代做程序编程语言jagged or stair stepped in objects that should appear smooth. In ray tracing applications, anti-aliasing can be performed by tracing multiple rays per pixel.  Your approach should subdivide each pixel into the, say, 3x3 grid, casting one ray per subpixel. The resulting color should then be the average color of the 9 rays (for a 3x3). A 3x3 will provide a more refined image than 2x2 or 1x1 grids.What to submit

● Your source code. A zip file containing your MS VS Project (or XCode project). Make sure that your code is backed up prior to zipping it up. Your zip file should be created using the top-level directory of the project (the one that contains the CSE386.sln and CSE386.xcodeproj). You should then unzip your zip file and verify that others can open up your project and run it using MS Visual Studio or XCode. An incomplete zip file will incur a 10 point deduction.
○ MS Visual Studio users: To make the zip file compact, delete the following directories:
■ CSE386/.vs   -- This is a hidden directory, which requires you to configure the file manager to see hidden files/folders.
■ CSE386/packages
■ CSE386/x64   and    CSE386/Release    and     CSE386/Debug
■ CSE386/CSE386/x64   and   CSE386/CSE386/Debug and CSE386/CSE386/Release
■ After this, your zip file should be at most a few MB. Make a good faith effort to create a compact zip file; however,
○ For XCode developers, simply leave all the files intact.
● A basic report that itemizes the features that work. Use the following template: ray tracing project report. Not submitting a report will incur a 10 point deduction.
● Video demonstration of your project. This video will be less than 7 minutes long and will demonstrate all the features of your program.  Not submitting a video will incur a 10 point deduction. Use the script. below when creating your video.Instructions for Video Submission
Create a video that is at most 7 minutes long. (It is OK if your video is 7:20 but it certainly should not be 10 minutes.) You should assume the audience is the instructor and is knowledgeable about terminology and techniques so you may simply refer to the techniques that you are demonstrating. It is your responsibility to ensure that all of your features are demonstrated clearly.
General notes regarding your video:
a. On MS VS, run your code using Release mode, as it will be faster than Debug mode. (I don’t have reliable instructions for doing this in XCode.)
b. Make sure that the axes are visible
c. Call out the keystrokes as you make them (e.g., “turn off first light”, “increase x”, etc).
d. Make sure that your project is running before recording.
e. Make sure that the objects you place in the scene are situated in a way that the viewer is convinced that the rendering is done properly. Set material properties, positions, lights, etc. appropriately to achieve this goal.
Script. to follow:
a. Announce your name and give a brief summary of what aspects of your project work and those that do not.
b. Display your source for Raytracer::raytraceScene and Raytracer::traceIndividualRay (if applicable). Walk through the code, describing the main parts of the code. Assume that you are explaining this to the instructor. This part should be 30 seconds.
c. Demonstrate lighting
i. Basic lighting
1. Make sure only one positional light is active. Make sure attenuation is turned off.
2. Talk about your shapes and convince the viewer that the shading on your objects is accurate. By moving the light around. For example, increase/decrease x/y/z several times, show that the changes to the objects’ shading that are consistent with the light moving toward the positive x axis.
ii. Demonstrate shadows
1. Identify several properly rendered shadows. Move the light to verify the shadows are properly updated.
iii. Spotlight
1. Turn off the positional light and turn on the spotlight.
2. Move the spotlight's position. Identify the parts of the scene that suggest your spotlight is correct.
3. Move the spot light’s direction. Identify the parts of the scene that indicate that your spotlight is correct.
4. Turn on positional light and show that both lights work together to jointly brighten parts of the scene. That is the spotlight and positional light add up.
d. Demonstrate Objects
i. Point out each of the required 3D shapes.
ii. Point to your open-ended cylinder and show that both the inside and outside of the cylinder is rendered properly.
e. Demonstrate Textures
i. Point out the textured object.
f. Demonstrate Transparency
i. Identify the transparent object and indicate why it is correct.
ii. Put the transparent plane in motion to demonstrate that it works across a range of situations.
iii. Turn off the transparent plane  when it is out of the way.
g. Demonstrate advanced features
i. Reflections
ii. Anti-aliasing

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
