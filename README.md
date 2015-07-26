# SABcmd
Bash based command line interface for SABnzbd. 

This script acts as an api client to SABnzbd. It offers basic
operations, such as adding/removing nzb files to/from SABnzbd.

The features are quiet basic, but feel free to contribute new 
features or bug fixes.

Installation
--------------

Copy sabcmd to $PATH (e.g. /usr/local/bin).
Copy sabcmd.conf.sample to /etc/sabcmd.conf or ~/.sabcmd.conf and edit.

    sudo cp sabcmd /usr/local/bin/
    cp sabcmd ~/.sabcmd.conf
    vim ~/.sabcmd.conf

Usage
-------
SABcmd can be invoked on the command line, passing commands and parameters.

    Usage: sabcmd <command> <parameters>
    
       Commands:
         - status      : Print queue status
         - long-status : Print queue status (verbose)
         - add         : Adds a nzb to the queue
         - delete      : Deletes a nzb from the queue
         - pause       : Pauses SABnzbd
         - resume      : Resumes a paused SABnzbd
         - restart     : Restarts SABnzbd

       Parameters:
         - --category/-c : The category to add a nzb to.
         - --nzb/-n      : Path or url to the nzb file to add.
         - --target/-t   : The queue target to operate on.
         
       Examples:
         - sabcmd status
         - sabcmd add http://here.is.my.nzb/ubuntu14_04.nzb
         - sabcmd add /tmp/here.is.my.nzb/ubuntu14_04.nzb
         - sabcmd delete ubuntu14_04

Contributing
-------
Contributions and feature requests are always welcome!

If you have any additions, examples or bugfixes ready, feel free to create a pull request on GitHub. The pull requests will be reviewed and will be merged as soon as possible. To ease the process of merging the pull requests, please create one pull request per feature/fix, so those can be selectively included in SABcmd.
