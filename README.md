[inc_CMakeScripts](https://github.com/InCom-0/inc_CMakeScripts) is a collection of CMake script obtained from other sources.

### How it works ###
1. The 'default' branch contains nothing except this README. This is intentional.
2. The 'main' branch contains the individual directories containing the CMake scripts
3. The original upstream sources of the CMake scripts are included via git submodules in other (one or more) branches
4. The 'main' branch 'handpicks' only the files needed from the other branches and updates them using automated workflow


### How to use: ###
1. Add the 'main' branch of this repository as a subtree into a repository where you need these CMake scripts using 
    * `git subtree add --prefix=cmake https://github.com/InCom-0/inc_CMakeScripts.git main --squash`
    * You can of course change the prefix directory to anything else. However, it is common practice to use 'cmake' directory for this purpose
    * The above command will fetch the content of that branch into a working directory, squash past commits and make a merge commit to current branch of your project

2. You can later update the script via (probably never necessary as the scripts are more or less stable)
    * `git subtree pull --prefix=cmake https://github.com/InCom-0/inc_CMakeScripts.git main --squash`


### Why do it in this rather convoluted way: ###
1. Keep the CMake scripts stored locally in 'consuming' repos
2. Not having to use submodules in 'consuming' repositories
3. Still being able to 'de facto' reference the original upstream sources of these scripts (but only through branches in this repo not meant to be used by consumers)
4. Enable updates of said scripts (by pulling the main branch again) 
5. Making all the above possible while also being able to put other custom scripts inside the same directory