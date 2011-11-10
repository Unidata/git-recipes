## Eclipse Egit ##

Often times, developers prefer using their IDEs to interact with a version control system. Here are some basic instructions for installing egit using the IDV as an example.

+ Get the eclipse egit plugin via the Eclipse marketplace that is available within eclipse.
+ In eclipse,  File &rarr; Import &rarr; Projects from git. Point to https://github.com/Unidata/IDV.git. Be patient at this step. See [here](http://www.vogella.de/articles/EGit/article.html#respository_checkoutproject).
+ This will eventually take you to the new project wizard. Make sure your IDV git repository and the eclipse project directory are co-located in the same directory. Do not choose a different directory project for the git repository.
+ (Optional) For simplicity, copy over your eclipse .classpath file from your existing *svn* IDV rep to the root of the IDV git project.
