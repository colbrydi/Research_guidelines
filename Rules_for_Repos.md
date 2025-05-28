# Dirk's Guidelines for Project Code Repositories

## Projects need to be Safe
Projects must prioritize safety in terms of data handling, ethical considerations, and compliance with legal and institutional standards. All members of Dirk's Project teams must read and follow [MSU usage guildines](https://tech.msu.edu/about/guidelines-policies/aup/).

* Projects should be developed and used in ways that are ethically sound. This means avoiding harm, respecting user privacy, and considering the broader social impact of the work.
* Ensure that all sensitive data is handled securely. This includes encrypting data when necessary, avoiding the inclusion of confidential information in code repositories, and following best practices for data protection.
* Always give credit where it is due. If you use code, data, or ideas from others, make sure to cite them appropriately in your documentation and comments.
* Adhere to all relevant laws, regulations, and institutional policies. This includes software licensing, data usage agreements, and any applicable research ethics guidelines. 

## Projects needs to be Portable
Portability means that the project can be moved between users and systems. 

* Use version control (ex. git) to track and share your ASCII code. Commit early and often.
* Never use absolute Paths. Always use relative paths. i.e. never use paths that start with root (```/```) on Mac/Linux or a directory letter (ex: ```c:/```) on windows. Instead, paths should start with current directory(```.```) parent directory (```..```) or home directory (```~```). 
* Avoid "hard coding" algorithm parameters.  Instead use defaults but allow flexibility in setting parameters using things like input arguments.
* Defaults should work "by default" and present a reasonable guess for all inputs. 
* Never use spaces in filenames.  It may work on your machine, but spaces always seem to cause problems when moving code around. 
* Use minimum number of constraints when generating ```requirements.txt,``` ```enviornment.yml``` or similar files. 
    * Only include top level required libraries and let the dependencies automatically get added by the installer.
    * Avoid using exact version numbers and let the installer pick them. If you must pick a version number use a >= option to be the most flexible or <= if there is a problem with a newer version.  
    * Test install instructions on more than one architecture. Ideally Windows, Mac and Linux.
* Use a common "Default" architecture that is available to everyone using the project. For example, if it is internal to MSU you can use the MSU HPCC.  If it is external to MSU try Google Collab.  Actually, getting notebooks to work by default in Google Collab is a great idea (assuming NDAs are followed).
      
## Projects need to be Reproducible
Reproducability means that the code generates the same results for everyone. This allows people to start where someone else leaves off.

* When appropriate include descriptions of the Hardware and OS where most of the development was conducted. This will help future developers debug problems. 
* Automate the install whenever possible. Things like makefiles and bash scripts can be very helpful.  Just make sure they are well documented.
* Best install instructions are single command but with details on what that command is doing so that it can be easily debugged or changed. 
* Include a second ```enviornment.yml``` or ```requirements.txt``` file with a different filename that includes the exact working environment.  This is intended as a reference to help debugging if something goes wrong with the more portable install.

## Projects need to be Robust
Robust means that the code isn't sensitive to small changes which will make it easy to update.  
* Use modular design by breaking the code down into logical and independent parts. 
* Establish success metrics for evaluating code. These metrics should be able to clearly measure if the system is getting better.  
* Avoid copy/paste of words/code.  Try to write something once and reference it in other places.  Use libraries (ex ```py``` files) to store redundant code. This also goes for documentation.  Don't have the same instructions in multiple places. 
* Logically separate interface code from model code and data read/write code.
* Interface development should go in order: programming interface first, command line interfaces second, graphical user interfaces third. Jumping directly to the GUI design will skip keep steps and make the code overly complex.  Each interface step should build off the other to help make the code robust and clean. 
* Whever possible write unit testing code and build automated checks.

## Projects need to be Literate
Literate means that the project is well documented and communities what it is supposed to do and why.

* Know your potential audience and avoid or document assumptions about what they know and don't know.
* Name files/variables/functions appropriately. it should be clear what an object is for by it's name.
* Avoid too many folders such as folders with single files.  If there is a single file in a folder, ask yourself why the folder needed?
* Assume the user will read the ```README``` file as the starting point. The file should guild the user on how to install and get the project working. 
* Every code file should (at a minimum) have a comment at the top with a title and a description of what the file does and why.
* Keep things clean
    * Don't commit unnecessary files. For example, files that are generated by code typically are not inclded in the repsoitory.  
    * Use ```.gitignore``` file.
    * NEVER ever use ```git add *```
    * Organize the folders in a matter that makes sense.
    * Whenever possible use established coding standards.

## Use Git as Git was intended
* Use a premade ```.gitignore``` file from the internet for the coding language you are using. 
* Avoid adding data to a git code repository. This includes input data, intermediate data and output data.  Data should be stored someplace else and referenced. Instructions should be clear how to bring data into repository to use. 
* Like data, never add binary files (especially ones that change). This includes files like word docs and excel docs.  Pdfs and images can be okay if they are fixed and not changing very often. Much better is markdown and other plane text formats.
* Use the [bfg](https://rtyley.github.io/bfg-repo-cleaner/) tool if you need to delete a big or secure file

## Use Jupyter as Jupyter was intended
* Learn Markdown and Use it. Include pictures and links in your comments. 
* Every jupyter notebook should have a Markdown cell at the top with a title and a description of what the file does and why.
* Whenever possible use "Kernel Restart and Clear all output" before adding and committing a jupyter notebook to a git repsitory. This will remove the binary data and make it cleaner for git. 
* Develop modules and classes in jupyter for rapid API development and move them to python libraries to help with robustness. 

***NOTE:*** There are exceptions to every rule.  However, it is important to understand why the rule exists before you can understand when it is okay to make an exception.
