# IPaddressFeed2CheckPointAPI
Adding a IP Address feed (CIDR) into Checkpoint Objects (here Office 365)


How to use:
Copy Script to file system (e.g. create a folder under root “scripts” or so) - Edit script at the header (only) (most important: upper half, lower half can remain, as this are temporary files only – created during script runtime and deleted at the end)

In GAiA Web UI just add Job Schedule for this
example:
sh /scripts/o365-api | /usr/bin/tee -a /scripts/o365_logging 2>&1 | /usr/sbin/sendmail --domain=<mail domain> -f <sender address> -v <recipient address> --host=<mail relay> 2>&1
Adds logging entries to a file "o365_logging" and sending a mail with the content

Adapting 
Script can be used for any other feed, where network addresses are in CIDR format.
i.e. the newer one planned API feed from Microsoft - described here:
https://support.office.com/de-de/article/verwalten-von-office-365-endpunkten-99cab9d4-ef59-4207-9f2b-3728eb46bf9a?ui=de-DE&rs=de-DE&ad=DE#ID0EACAAA=4._Web_service

As the script already does a diff between existing objects and those downloaded, the full list should be used...
Objects are automatically removed from group and from Check Point mnanagement, when they are not part of the feed.

