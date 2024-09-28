# ZPool & SMART status report with FreeNAS config backup
Original script by joeschmuck, modified by Bidelu0hm, then by melp

Preview of the output here: http://i.imgur.com/t9Mtqyt.png

## Installation

### Requirements

Your Truenas installation needs to be able to send emails. Please check the SMTP/Email config in the Truenas General settings.

### Core

TODO - add core specific configuration

### Scale

 - Clone this repo at the location of your choice on your Scale system
 - Add a cron job to run report.sh, under System settings -> Advanced -> Cron Jobs
 - In the command field, use bash to invoke report.sh: ```(cd your/git/rpo/location/ && bash report.sh)```
 - Run as root, as of Dragonfish

**At a minimum, you will need to enter your email address in user-definable parameter section.** Feel free to edit other user parameters as needed.

**Version: v1.3**

**Changelog:**

*v1.3:*
- Added scrub duration column
- Fixed for FreeNAS 11.1 (thanks reven!)
- Fixed fields parsed out of zpool status
- Buffered zpool status to reduce calls to script

*v1.2:*
- Added switch for power-on time format
- Slimmed down table columns
- Fixed some shellcheck errors & other misc stuff
- Added .tar.gz to backup file attached to email
- (Still coming) Better SSD SMART support

*v1.1:*
- Config backup now attached to report email
- Added option to turn off config backup
- Added option to save backup configs in a specified directory
- Power-on hours in SMART summary table now listed as YY-MM-DD-HH
- Changed filename of config backup to exclude timestamp (just uses datestamp now)
- Config backup and checksum files now zipped (was just .tar before; now .tar.gz)
- Fixed degrees symbol in SMART table (rendered weird for a lot of people); replaced with a *
- Added switch to enable or disable SSDs in SMART table (SSD reporting still needs work)
- Added most recent Extended & Short SMART tests in drive details section (only listed one before, whichever was more recent)
- Reformatted user-definable parameters section
- Added more general comments to code

*v1.0:*
- Initial release

**TODO:**
- Fix SSD SMART reporting
- Add support for conveyance test
