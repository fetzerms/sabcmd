# SABcmd
Bash based command line interface for SABnzbd. The goal of this
project is to nearly run without dependencies. So it could be run
on embedded devices such as routers or in restricted chrooted environments.

If you have python available, https://github.com/TobiasTheViking/sabcli
is worth a look aswell.

This script acts as an api client to SABnzbd. It offers basic
operations, such as adding/removing nzb files to/from SABnzbd.

The features are quiet basic, but feel free to contribute new 
features or bug fixes.

Installation
--------------

Copy sabcmd to $PATH (e.g. /usr/local/bin).
Copy sabcmd.conf.sample to /etc/sabcmd.conf or ~/.sabcmd.conf and edit.

    sudo cp sabcmd /usr/local/bin/
    cp sabcmd.conf.sample ~/.sabcmd.conf
    vim ~/.sabcmd.conf

To make the script work, curl and xmlstarlet need to be installed.

    Ubuntu/Debian: sudo apt-get install curl xmlstarlet
    CentOS: sudo yum install xmlstarlet curl

Usage
-------
SABcmd can be invoked on the command line, passing commands and parameters.

    Usage: sabcmd <command> <parameters>
    
       Commands:
         - status      : Print queue status
         - long-status : Print queue status (verbose)
         - count       : Print the count of the queue
         - add         : Adds a nzb to the queue
         - delete      : Deletes a nzb from the queue
         - change      : Changes the priority and/or category of a nzb.
         - pause       : Pauses SABnzbd
         - resume      : Resumes a paused SABnzbd
         - restart     : Restarts SABnzbd

       Parameters:
         - --category/-c : The category for the nzb.
         - --priority/-p : The priority for the nzb. 
                           Possible values: paused, low, normal, high and force.
         - --nzb/-n      : Path or url to the nzb file to add.
         - --target/-t   : The queue target to operate on.
                           Can be: nzo_id, nzb-name or number

                           Caution: When passing a nzb-name, the operations
                                    will affect all matching queue entries.

         
       Examples:
         - sabcmd status
         - sabcmd count
         - sabcmd add --nzb http://here.is.my.nzb/ubuntu14_04.nzb --priority low
         - sabcmd add --nzb http://here.is.my.nzb/ubuntu14_04.nzb --priority low --category test
         - sabcmd add --nzb /tmp/here.is.my.nzb/ubuntu14_04.nzb
         - sabcmd change --target ubuntu14_04 --category test
         - sabcmd change --target ubuntu14_04 --priority high
         - sabcmd delete --target ubuntu14_04
         - sabcmd delete --target SABnzbd_nzo_wRDhlV
         - sabcmd delete --target 2


Note on add command
-------
The add command takes three types of --nzb arguments:

- Local files: Those will be uploaded to SABnzbd.
- Remote files: Files that are local to the SABnzbd instance.
- Urls: A url to the NZB to add.

The procedure is as follows:

- If the --nzb argument starts with http, the url is passed to SABnzbd.
- If the --nzb argument is a file path, and if the file exists locally, it is uploaded to SABnzbd.
- If the --nzb argument is a file path, and does not exist locally, it is passed to SABnzbd.

Contributing
-------
Contributions and feature requests are always welcome!

If you have any additions, examples or bugfixes ready, feel free to create a pull request on GitHub. The pull requests will be reviewed and will be merged as soon as possible. To ease the process of merging the pull requests, please create one pull request per feature/fix, so those can be selectively included in SABcmd.
