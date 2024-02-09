## Static Acquisition Procedure
Document -> Remove Subject Drive -> Prepare Drive -> Connect Write-Blocker -> Prepare Target Drive
- There can be *software* write-blockers and *physical* write-blockers

## FTK Imager
AccessData ForensicToolkit
- Can be used to make copy of disks
- Can also pull data from memory

### Demo
File -> Create Disk Image -> Select Physical Drive -> Select Virtual Drive -> Finish -> Add Image Destination -> Raw -> Random Shit in Here -> Create Destination Folder on Desktop ->  Image Filename: Ch3 -> Finish -> Check verify images -> Start

## Hashing Commands
Linux
- md5sum {filepath}
- sha1sum {filepath}
Windows
- Get-FileHash -algorithm {algo} {filepath}

## Raid Types
Raid 0 - Striping
Raid 1 - Mirroring
Raid 2 - Striping with Parity
- Parity replaces part of lost data from disk
Raid 5 - Block level striping with distributed parity

## Remote Network Acquisition
Remotely collective drive information 
