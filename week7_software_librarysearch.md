# Week 7

## Managing Software

I've maintained Linux servers, so this part is familiar. Installing software is easy in my experience. It's those dependecies that will get you! Practice is still good.

#### Common commands
- `sudo apt update`: check for updates. **Do this each week and before installing anything.**
- `sudo apt upgrade`: upgrades out of date packages.
- `apt search (package name)`: search for package.
- `apt show (package name)`: displays information about the package.
- `sudo apt install (package name)`: Installs package. 
- `sudo apt clean`: removes unnecessary files.

## Library Search

Z39.50 is standard protocol in libraries for sharing, querying, and retrieving bibliographic information. 

### Yaz

A tool to retrieve this library information. 

`yaz-client`: Open Yaz

`open saalck-uky.alma.exlibrisgroup.com:1921/01SAA_UKY`: Connect to library's OPAC or discovery service. 

#### Example Find commands

`f @and @attr 1=21 "cybersecurity" @attr 1=21 "python"`: Searches in the Subject heading and uses the @and to find multiple phrases or words. 
`find @attr 1=4 "linux servers"`: Searches the phrase in the title. 
`f @attr 1=1016 "linux commands"`: Searches the phrase in all fields. 


#### View results

`show 1`: displays first result. Change number to change which result to display. 


