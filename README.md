# MC Texture Generator

A Java program that programatically generates textures generated by certain versions of Minecraft at runtime, and then saves them to individual files.

Currently, this program generates:

- All textures generated by Minecraft 4k-1
- All textures generated by Minecraft 4k-2
- All frames of the gear rotation animation
- All frames of the nether portal animation
- The checkerboard "missing texture" textures

The program can also generate some non-deterministic textures, if a valid value for the command line parameter -nonDeterministicFrames is passed to it. Currently, this program can generate the following non-deterministic textures:

- Water textures from Minecraft Classic 0.0.19a
- Lava textures from Minecraft Classic 0.0.19a and 0.0.22a
- Fire textures
- Certain "missing texture" textures which use text rendering based on the the current JVM / system

## How to generate the textures.

Make sure to have a Java runtime environment of 6 or higher installed on your computer. The easiest way to run this program is just to double click the .jar file, which will generate and save all textures to a folder named "GeneratedTextures". The .jar file can also be run from the command line. Doing so will allow you to see log output when generating the textures, which can be useful if you need to debug anything. When this program is run from the command line, the "GeneratedTextures" folder will be placed at the current directory that your command line is in. The command line parameters you can pass are:

- -nonDeterministicFrames (integer n): Generates n frames of each non-deterministic texture. Otherwise, no non-deterministic textures are generated.
- -randomSeed (long n): Sets the starting seed for each random number generator used by textures generated from non-deterministic generators. Otherwise, a random starting seed is used.

Example command line usage:

- Running `java -jar MCTextureGenerator.jar` generates all deterministic textures.
- Running `java -jar MCTextureGenerator.jar -nonDeterministicFrames 1024` generates all deterministic textures, and 1024 frames of all non-deterministic textures.
- Running `java -jar MCTextureGenerator.jar -nonDeterministicFrames 1024 -randomSeed 100` generates all deterministic textures, 1024 frames of all non-deterministic textures, and sets the seed of the random number generator for each non-deterministic texture generator to 100.

## Why have a dedicated program for this?

The idea behind this program is to create an improvably accurate source for these textures - if this code contains any mistakes, the mistakes can simply be fixed, and the textures will then be generated accurately. The same improvement in accuracy cannot be achieved for an inaccurate screenshot, or a file accidentally saved in a reduced resolution or color depth.
