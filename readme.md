# Alfresco Support Tools for the new Admin console in Alfresco 4.2    
    
    
This add-on has been designed to work only in **Alfresco Enterprise 4.2** using JDK7 and Tomcat7.  
It probably won't work on Alfresco Community Edition due the lack of JMX connectivity.  
From the client side has been tested to work with current versions of Firefox, IE and Chrome only. 


## License

Copyright (c) 2013, Alfresco Software Ltd. October 2013

**Author:** Antonio Soler, antonio.soler@alfresco.com

Alfresco is free software: you can redistribute it and/or modify
it under the terms of the GNU Lesser General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

Alfresco is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Lesser General Public License for more details.
See <http:www.gnu.org/licenses/>.

_**THIS SOFTWARE IT IS NOT DIRECTLY SUPPORTED OR MAINTAINED BY ALFRESCO LTD.
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR    
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,       
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE   
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER        
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, 
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN      
THE SOFTWARE.**_

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

## Releases

It's possible to download the last release here

## Installation
There are two options to install the tools using the AMP: the standard and the hot deploy.

1. ###Standard

  *	Place the _support-tools-*.amp_ file into your Alfresco _amps_ folder 
  * Run the script: **bin/apply-amps.[sh|bat]** with the **-force** switch.
  
  Alternatively it is possible to: 
  *	Execute the following command (amending the paths to your case):
  
    		java -jar ./bin/alfresco-mmt.jar install ./amps/ ./tomcat/webapps/alfresco.war -force -verbose
  
  *	Clean out the currently deployed web application by removing :
  	* tomcat/webapps/alfresco/*
  	* tomcat/work/*
  	* tomcat/temp/*

2. ###Hot-Deploy

  This method lets you use the tool without rebooting your application server.
	* Execute the following command (amending the paths to your case):

			java -jar ./bin/alfresco-mmt.jar install ./amps/support-tools.amp ./tomcat/webapps/alfresco -force -verbose -nobackup
    
		Be aware it is mandatory to point the installation to the alfresco webapp folder, differently from the war used at point 1, and to use the **-nobackup** switch. 
	
	* Reload webscripts by going to:
	
			http:[host]:[port]/alfresco/service/index
	
	* click on _"Refresh Web Scripts"_
	
  **Important Note:** The Tail-Log tool won't cache log entries until the next restart, but the rest of the webscripts will work.


## Usage
Go to the URL
    
    http:[host]:[port]/alfresco/s/enterprise/admin/
    
New scripts will appear under the **Support Tools section**.

## Acknowledgments:
**Special thanks to:**  
* Mike Farman for his support on this project and parts of the code.  
* Marco Mancuso for his help on the development.  
* Jamie Allison for his code review, "polish" and improvements.  
* Will Abson for his useful advice.  
* The Smoothie Charts creators: 
	http:smoothiecharts.org/ the library from which was quite useful and fun to use

## Version history

 1.0 Initial Working version, some UI adjustments needed  
 1.1 Code Reviewed and commited to GitHub  
 1.2 UI improvements by Jamie Allison, added ajax to some webscripts for automation ("Active Sessions")   
	 Changed the general aspect of the "Scheduled Jobs" section, New tabs abd buttons on "Threaddumps"   
     Automated dist generation with Ant.  
 1.3. Added filesaver.js to fix the "save all" problem with IE8  
 1.3.1. Error in build xml caused to distribute jmxlogger library on 2 different locations, fixed   
 1.4. Added 2 new tools:  
	* Hotthreads: to detect which thread is consuming more CPU time  
	* JMX Settings: to find which beans have values overriden from the DB and revert them  
 1.4.1 Bugfix for HotThreads, missing hotthread ids caused an error  
 1.4.2 Bugfix for Activesessions, missing properties my cause display error on freemarker.   