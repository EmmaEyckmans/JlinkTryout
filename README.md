# JlinkTryout
Jlink tryout for the guild meeting



**What is jlink?**  
Jlink is Java’s new command line tool which allows you to link sets of modules (and their transitive dependencies) 
to create a run-time image. Java has always had dynamic linking, but with Java 9 there is now an optional static linking step. 
This is called link time (optional phase), and it happens between compile time and run time.
You can use the jlink tool to assemble and optimize a set of modules and their dependencies into a custom runtime image.

**Why would I be interested in jlink?**  
Jlink will allow you to both simplify and reduce the size of deployment. 
The days of having  to ship lots of jars and download the whole JRE/JDK are now long gone….
You can create a runtime image containing only the necessary modules to run an application
The JDK itself has been sorted into proper modules that allows you to cherry pick the ones you need.

**How to use it**  
jlink --module-path $modulepath$  
      --add-modules $modules$  
      --output      $output$  
* $modulepath$: path of directories containing the packaged modules (jar or jmod format)  
* $modules$: names the modules to add to the run-time image. These modules can, via transitive dependencies, cause additional modules to be added.
* $output$: directory that will contain the resulting run-time image
The result is a new directory $output$ containing essentially a Java runtime completely tailored to running your application. 
The folder contains a bin folder with an executable script directly launching your module (if you added the --launcher argument that is apparently).