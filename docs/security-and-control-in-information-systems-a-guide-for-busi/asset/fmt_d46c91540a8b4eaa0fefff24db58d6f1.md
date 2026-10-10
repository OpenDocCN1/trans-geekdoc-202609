
The simplest approach to keeping back-up copies of data is based on ‘generations’, as illustrated in [Figure 9.5](#ch9.xhtml#fig9_5). On 1 January, a back-up copy of data is made onto tape A. A week later the back-up is made on tape B, and a week later tape C is used. At this point, the installation has three back-ups. Only one of these is up to date, but in the event that anything should happen to it, the other two are available as ‘long-stops’. At this point, the tapes start to rotate, so that on 22 January tape A is reused, and becomes the most current copy. This ensures that at any given time there will always be three generations of tape: an elderly ‘grandparent’, a younger ‘parent’ and a new ‘child’. To improve the chances that at least one copy will always survive, the tapes are all stored in different locations. This could mean using other buildings belonging to the organisation, or a commercially operated secure vault service.

![Figure 9.5](images/fig9_5_C.jpg)

[Figure 9.5](#ch9.xhtml#R_fig9_5)

In practice, data back-up strategies need to be a little more sophisticated than this, for a number of reasons.

* Since full back-ups often involve huge amounts of data, it can be easier to work with *incremental* back-ups. These contain only the *changes* to data which have been made since a previous back-up. To re-create the data in its entirety, it is necessary to start with one full back-up, and add back all the incremental back-ups which have been made since.
* Other copying procedures may be in place for other purposes; for example, records may be regularly removed from the ‘live’ files on the main computer disks, and put into some form of archive. It may be assumed (perhaps quite wrongly) that the archiving provides protection against disaster. If the archives are not protected, they too must be included in the back-up plans, since they may be needed for legal reasons, or to assist with audit, or for long-term analysis required for management decisions.
* When data is live on the system it will be subject to the kind of access controls described in [Chapter 4](#ch4.xhtml). The data must continue to be protected once it is on the back-up tape (which will usually mean placing strict restrictions on the situations in which the tape can be used), and it must be possible to re-create the data in an exactly equivalent form on another system, so that the access controls will continue to work. Particular care must be taken to transfer files complete and intact, if they have been subjected to controls based on hashing or encryption.

In some cases the backing up of data seems pointless; for example, reference data used in planning or design work may have been obtained from external sources, making it easy to replace. Duplicate copies of some datasets may be held on the system, to serve different groups of users, or to improve system performance, and making duplicate backups of these seems excessive.

In a large installation, it may be worth the effort of sifting out such data. One way of doing this is by ranking it by ‘criticality’. Toigo ([1996](#reference.xhtml#ref_r223): 167) defines data with high criticality as that which supports vital business functions, or is required for legal or audit purposes, or which comprises proprietary information and trade secrets. Low criticality data, which occupies a lot of storage space in some organisations, can then be ignored.

Software usually accounts for much less storage space, and so there should be no problems in backing it up in its entirety. Particular attention must be paid to critical software, i.e. that which is unique to the business, and which handles core activities like inventory management and accounting. Nevertheless, it pays to make software back-up as comprehensive as possible, to avoid being caught out by inter-dependencies between programs, which are not always obvious. For example, a package may need to make use of data-compression utilities, without which it will be unable to open its files.

### 3. Premises
If the existing computer facilities are a mass of rubble, where do you go? This question should have been considered long before, and the answers incorporated into the DRP. To ensure availability, the alternative premises should be a long way away, increasing the chances that they will be unaffected by any wider disaster which may have engulfed the original site. However, this will slow down the recovery, as it will take longer to transfer staff, and any materials which have been salvaged.

### 4. Processors
Decisions about processors are closely linked with decisions about premises. Generally, stand-by sites can be grouped in three categories.

#### 1. Mutual
Agreement is reached with another site that space and computing power will be set aside, and will always be available in the event of a disaster. The idea is that the two parties each operate similar systems, but always allow for a certain amount of spare capacity, so they can, if necessary, provide back up for each other. This is an attractive option for two sites within the same organisation, especially if they are run as part of a single IT department. The situation can be more complicated if separate organisations are involved. Each party has, after all, to fund spare capacity for the other’s benefit, and it may be difficult to agree exactly how this should be paid for. Tensions may also arise because the installations, even if they were very similar initially, may need to develop in different directions in terms of their equipment or software.

#### 2. Warm or hot stand-by
A hot stand-by site offers facilities which closely match those available in the organisation’s own installation. This includes all the necessary power, cabling, telecommunications, air conditioning, and a complete set of computer equipment.

A site which offers more basic facilities may be known as a ‘warm’ site. Here the expectation is that not everything will be immediately available, but plans will have been put in place to bring in and activate whatever is needed within a matter of hours. Very few organisations can afford the luxury of either a hot or a warm stand-by site of their own, and this is a field for a few specialist commercial providers, who cover their costs by charging annual fees to subscribers. Even then, the small print of the agreement may state that there is no guarantee that the site will be available when needed, as in the case of snow damage at EDS.

#### 3. Cold stand-by
A cold stand-by site (sometimes called a ‘shell’ site) offers no more than space in which the computer service can be rebuilt from scratch. It will have adequate power supplies and some rudimentary telecommunications links, but little else. It will be up to the client to borrow or buy in processors, disks, and printers, and to arrange for any extra telecommunications links which are required.

Variations on this theme described by Barnes ([1999](#reference.xhtml#ref_r23)) include a retail bank which ran extra power and telephone cables into the staff canteen, so that this could be their cold site, and a scheme devised by a London publishing company, whereby a property agent undertook, for an annual fee, always to identify three vacant sites on his books which would make suitable cold sites, and which would be instantly available on a six-month lease.
