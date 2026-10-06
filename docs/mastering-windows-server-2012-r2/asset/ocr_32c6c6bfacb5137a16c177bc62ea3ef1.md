# CHAPTER 25 MIGRATING, MERGING, AND MODIFYING YOUR ACTIVE DIRECTORY

# PERFORMING AN IN-PLACE UPGRADE FROM A 2008 R2 (X64)-BASED AD

Performing an in-place upgrade involves these basic steps:

+   1. Prep the forest/s schema to be compatible with Windows Server 2012.
2. Prep the domain for Windows Server 2012.
3. Run the Setup program to upgrade the domain controller.

These steps are described in detail in the following sections.

# Prepping the Forest/Schema and Domain

When doing an in-place upgrade, not all of your domain controllers need to be the same version of Windows Server; a mix of Windows Server 2008 R2 and 2008 64-bit is acceptable (64-bit versions are supported for upgrade). However, FSMO roles are to be located on specific Windows Server 2008 or 2008 R2 controllers. The domain naming of the forest, which by default is the first domain controller in the forest, must be at a minimum Windows Server 2008 64-bit. The PDC emulator of each domain must be at this minimum version as well. These by default are the first domain controller in your domain

If you're going to upgrade only one domain in your 2008-based forest to Windows Server 2012, you have to change your forest and domain's schema before 2012 can install on the target controller. All domains in a forest share the same schema, so you have to change your entire forest's schema. This task is done on the forest's schema operations master FSMO.

Microsoft has made some changes to the adprep tool, mostly to the areas where it writes data and indicates what objects are published. The following links are to Tech articles that give you a breakdown of all entries. We recommend that you review these before running the adprep command in your production environment.

Forest-Updates http://tinyurl.com/c25AdPrepFW

Domain-Wise Updates http://tinyurl.com/c25AdPrepDw

Read-only Domain Controller Updates No updates to read-only domain controllers (RODC)

Schema Updates http://tinyurl.com/c25AdPrepSC

# Running adprep

Windows Server 2008 adprep built up the forest. If you are doing other migrations types (swing or domain migrations) when you add the Active Directory Services roles, you will run adprep as needed. You need to access your CD/ISO to start this process for an in-place upgrade. In order to successfully run the adprep command, make sure you have the appropriate credentials to run the command:

adprep /forest requires membership in the following groups:

+   * Schema Admins
* Enterprise Admins
* Domain Admins