### P2Builder

P2/Ant build scripts for constructing a private Eclipse-standard P2 update site.

#### Summary

P2Builder provides a light-weight script-based mechanism for constructing a private P2 update site for testing and internal use. Particularly useful where multiple plugins are required to be built, individual manual building is too time consuming, and other solutions, such as Maven and Tycho, are too heavy-weight or public. 

#### Features

Advantages

  1. Scripts are simple, short, clear Ant Xml files.
  1. Can be run directly from the Eclipse Package Explorer Run menu.
  1. Can be run as needed to build and deploy plugins to a repository.
  1. Can categorize plugins as deployed.
  1. Can invoke [ProGuard](http://proguard.sourceforge.net/) jar-processing as part of the plugin build process.
  1. Can merge a deployed private respository plugin into a separate, existing public respoitory.

Disadvantages

  1. Uses Ant, which is arcane.
  1. Uses the Eclipse PDE P2 Ant interface, which is byzantine.
  1. Completely unforgiving for any configuration errors.

#### License

P2Builder is licensed under EPL 1.0.  See the accompanying epl.html file. 

#### Dependencies

A current installation of Eclipse -- last tested with Eclipse Mars (4.5.0).

#### Notes

Preliminaries:

  1. Make sure the filenames and paths in `Action.properties` and `pde.customTargets.xml` are correct.
  1. Make sure the options selected in `pde.build.properties` are correct.
  1. Make sure the plugin references in `category.xml` are correct.
  1. Make sure the plugin Dependencies in the plugin being built are up to date -- minimum version numbers must match the current Eclipse installation.

Run:

  1. Make sure the filenames and paths in the p2Build-XXX.xml script are correct. 
  1. Run the script using `Package Explorer -> Run As -> Ant Build`

Utilities:

  1. p2Build-XXX.xml -- build scripts -- one per plugin project -- copy and edit as desired.
  1. p2Categorize -- runs the categorization process on the private repository.  
  1. p2Clean -- completely clears the private repository.
  1. p2Publish -- updates a public p2 respository from the private repository.
  1. p2Update -- runs a refresh/update process on the private repository.

Errors:

  1. If the final console message is that the build failed, recheck the Preliminaries -- all mistakes are fatal.
  1. The build process, even when it runs correctly, throws a lot of console error messages. Have to understand the Eclipse PDE P2 Builds processes to know what is significant and how to fix anything.
  1. If the build appears to complete normally, but the plugin, or the most recently built version, does not show for Installation or Update or is not categorized correctly, use the Reload button on the Eclipse `Available Software Sites` preference page to force a refresh of the relevant update site information.    
  