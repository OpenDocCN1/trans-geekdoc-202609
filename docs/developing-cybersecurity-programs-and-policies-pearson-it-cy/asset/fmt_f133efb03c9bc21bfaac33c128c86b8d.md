
# Data Destruction and Sanitization

NIST Special Publication 800-88 Revision 1 defines `data destruction` as “the result of actions taken to ensure that media cannot be reused as originally intended and that information is virtually impossible to recover or prohibitively expensive.” There are two methods of permanently removing data from a drive—disk wiping (also known as scrubbing) and degaussing.

## Disk Wiping

The `disk wiping` process will overwrite the master boot record (MBR), partition table, and every sector of the hard drive with the numerals 0 and 1 several times. Then the drive is formatted. The more times the disk is overwritten and formatted, the more secure the disk wipe is. The government medium security standard (DoD 5220.22-M) specifies three iterations to completely overwrite a hard drive six times. Each iteration makes two write passes over the entire drive; the first pass inscribes ones (1) over the drive surface and the second inscribes zeros (0) onto the surface. After the third iteration, a government-designated code of 246 is written across the drive, and then it is verified by a final pass that uses a read-verify process. There are several commercially available applications that follow this standard. Disk wiping does not work reliably on solid-state drives, USB thumb drives, compact flash, and MMC/SD cards.

## Degaussing

`Degaussing` is the process wherein a magnetic object, such as a computer tape, hard disk drive, or CRT monitor, is exposed to a magnetic field of greater, fluctuating intensity. As applied to magnetic media, such as video, audio, computer tape, or hard drives, the movement of magnetic media through the degaussing field realigns the particles, resetting the magnetic field of the media to a near-zero state, in effect erasing all the data previously written to the tape or hard drive. In many instances, degaussing resets the media to a like-new state so that it can be reused and recycled. In some instances, this simply wipes the media in preparation for safe and secure disposal. The National Security Agency (NSA) approves powerful degaussers that meet their specific standards and that in many cases utilize the latest technology for top-secret erasure levels.

## Cryptographic Erase

`Cryptographic Erase` is a technique that uses the encryption of target data by enabling sanitization of the target data’s encryption key. This is done to leave only the cipher text on the media and preventing read-access, because no one should have the encryption key. It is common for storage manufacturers to include integrated encryption and access control capabilities, also known as self-encrypting drives (SEDs). SEDs feature always-on encryption that ensures that all data in the storage device is encrypted. In practice, cryptographic erase can be executed in a fraction of a second. This is a great benefit because nowadays other sanitization methods take more time in large storage devices. Cryptographic erase can also be used in addition to other data destruction methods. You should not use cryptographic erase to sanitize data if the encryption was enabled after sensitive data was stored on the device without having been sanitized first. In addition, you should not use cryptographic erase if you are not certain if sensitive data was stored on the device without being sanitized prior to encryption.

## Destroying Materials

The objective of physical `destruction` is to render the device and/or the media unreadable and unusable. Devices and media can be crushed, shredded, or, in the case of hard drives, drilled in several locations perpendicular to the platters and penetrating clear through from top to bottom.

Cross-cut shredding technology, which reduces material to fine, confetti-like pieces, can be used on all media, ranging from paper to hard drives.

It is common for organizations to outsource the destruction process. Companies that offer destruction services often have specialized equipment and are cognizant of environmental and regulatory requirements. The downside is that the organization is transferring responsibility for protecting information. The media may be transported to off-site locations. The data is being handled by non-employees over whom the originating organization has no control. Selecting a destruction service is serious business, and thorough due diligence is in order.

Both in-house and outsourced destruction procedures should require that an unbroken predestruction `chain of custody` be maintained and documented and that an itemized post-destruction certificate of destruction be issued that serves as evidence of destruction in the event of a privacy violation, complaint, or audit. NIST Special Publication 800-88 Revision 1 mentions that destructive techniques also render a “device purged when effectively applied to the appropriate media type, including incineration, shredding, disintegrating, degaussing, and pulverizing.”

## In Practice

### Secure Disposal Policy

#### Synopsis
All media must be disposed of in a secure and environmentally sound manner.

#### Policy Statement
* The Office of Facilities Management and the Office of Information Security are jointly responsible for determining the disposal standards for each classification of information.
* Devices or media containing “protected” or “confidential” information must not be sent off-site for repair and/or maintenance.
* The standards for the highest classification must be adhered to when the device or media contains multiple types of data.
* A chain of custody must be maintained for the destruction of “protected” and “confidential” information.
* A certificate of destruction is required for third-party destruction of devices or media that contains “protected” and “confidential” information.
* Disposal of media and equipment will be done in accordance with all applicable state and federal environmental disposal laws and regulations.

## Stop, Thief!

According to the Federal Bureau of Investigation (FBI), on average, a laptop is stolen every 53 seconds, and one in ten individuals will have their laptop stolen at some point. The recovery statistics of stolen laptops is even worse, with only 3% ever being recovered. This means 97% of laptops stolen will never be returned to their rightful owners. The Ponemon Institute has conducted several studies and reported that almost half of laptops were lost or stolen off-site (working from a home office or hotel room) and one third were lost or stolen in travel or transit. The statistics for mobile phones and tablets is even worse.

The cost of lost and stolen devices is significant. The most obvious loss is the device itself. The cost of the device pales in comparison to the cost of detection, investigation, notification, after-the-fact response, and economic impact of lost customer trust and confidence, especially if the device contained legally protected information. The Ponemon Institute “2017 Cost of Data Breach Study: Global Overview” (`https://www-01.ibm.com/common/ssi/cgi-bin/ssialias?htmlfid=SEL03130WWEN`) calculated the average business cost of a breach in the United States to be $141 per record across all industries.

Consider this scenario: A laptop valued at $1,500 is stolen. A file on the laptop has information about 2,000 individuals. Using the Ponemon conclusion of $141 per record, the cost of the compromise would be $282,000! That cost doesn’t include potential litigation or fines.
