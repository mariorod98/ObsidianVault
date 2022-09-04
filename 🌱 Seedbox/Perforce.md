up::
tags:: #state/seedling #on/VSC

# Perforce

## What is Perforce?
Perforce is an enterprise [[Version Control System]] (VSC) in which users connect to a shared file repository. 

Perforce uses the **Perforce Versioning Service** (PVS) to manage shared file repositories (**depots**). The service maintains a database to track change logs, user permissions, and which users have which files checked out at any time. This information is known as **metadata**. 

To communicate with this service, you must use one of the different perforce client applications. These applications enable you tu check files in and out, manage conflicts, create branches, etc. Perforce applications include:
- P4, the Perforce Command-Line Client.
- P4V, the Perforce Visual Client.
- P4Web, the Perforce Web Client.
- Plug-ins that work with commercial IDEs.

With Perforce, you never work directly on files in the depot. Instead, you use the applications to manage your **client workspace**, which contains a local copy of a portion of a depot.

Therefore, Perforce has a client-server architecture, where you connect from your computer to the PVS to have access to your depot. 

## How does Perforce work?
In Perforce, all the files in your local workspace are read-only. To modify a file, you must first **check out** the file in the depot. 

Each file can only be check out by one user. This ensures that you will be the only user able to modify the file, as the other won't be able to check it out. Moreover, the PVS will show which files are check out by which user.

Checking out a file will add it to the current **changelist**. Once you have submitted that changelist, the file will be **checked in** and others users will be able to check it out.


## Perforce concepts
### Depot
A **depot** is a file repository hosted on the Helix Core Server. It is the top-level unit of storage for source files (aka *depot files*). It contains all versions of all files ever submitted to the depot, including deleted files.

The files in a depot are organized in directory trees, 

It is [[Git]]'s equivalent to a repository. 

### Changelist
Similar to the *stage* in [[Git]], perforce uses the **changelist** to track local changes to your **client workspace** that are not yet synced to the depot. The changelist serves two purposes:
- to organize your work into logical units by grouping related changes to files together.
- to guarantee the integrity of your work by ensuring that related changes to files are checked in together.
For example, if you are working on a change to some software that requires changes to three files, open all three files in one changelist.

A changelist can be *pending* if it has not yet been submitted to the depot. Or it can be *submitted* if the changes have been commited.


## Initializing a depot

## Adding files to a depot

---
Planted: 2022-09-04
Last tended: 2022-09-04