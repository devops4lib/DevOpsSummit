Problem statement:
* What do I do with these bagit bags? They are large, with AV content.


Solution providers:
* Duracloud
* APTrust
* Artifactual
* Arkivum
* Chronopolis
* MetaArchive (sort of like LOCKSS)

"It can't go in the cloud because that doesn't provide 'archival' storage"

TRAC certification: "Trusted Repository…" something


Penn uses git annex repositories, puts 2ndary copies in glacier.


NYU: Isilon in manhattan mirrored to syracuse. Backup to tape (dropping this and moving backup to S3). Apparently Columbia relies on Isilon's internal fixity checking.


Re: trusting amazon: You have to run fixity checking on the cloud in order to be able to confidently recover from it. Run checks from an amazon instance to save on network transfer fees.


Check all data, not just random files.


Archivists' concern about encryption is that technologies change and 100 years in the future you may not be able to access the file.


Isilon does block-level fixity checking, but cannot report at the file level.


Storage size. Number of objects. Size of objects. These all affect the cost of fixity checking in the cloud.


Anything over a petabyte Amazon will cut a deal. Work with an amazon rep or vendor to work out pricing.


Amazon does have HIPA certification, and other types of certifications for storing data. We should be able to trust Amazon that they are running reliable checksums.
* Does this guarantee the data will never go outside the US en route to us? You can set up a custom S3 endpoint in your VPC.


How do we figure out what destination certain types of objects should have?
* Things we don't necessarily need to keep around a long time. e.g. a patron requests a scan of 13 pages of a popular book.
* vs. things that are unique and irreplaceable.
* It would be helpful to identify different destinations for different types of resources.


Archivematica runs on a server; you give it access to all your storage everywhere. It takes care of moving data from place to place and running tasks on it, e.g. fixity, re-encoding. Everything is a microservice, which means lots of flexibility but also lots of complexity and can be brittle.


Automatic recovery.
* Tension between trusting the systems vs. urge to intervene when corruption is detected.
* Rather than checking all the files every day, a better strategy is to trust the storage to do its job.
* Fear of trusting institutional memory to a black box is valid.


If I put a copy on amazon and a copy on azure, and i lose a file on each. How do you get the good files from one system onto the other.
* Regular fixity checking / audits.


A mirrored isilon:
* this is mostly an availability strategy.
* A corrupted bit will not mirror, but a user error (accidental deletion) will be replicated.
* Use with a backup / preservation storage location as well.


Reasons for storing uncompressed data:
* If you get bitrot it's limited to one portion of the file, whereas if it's compressed bitrot could make decompression impossible or spread the loss across the whole file.
* technology could change over time rendering compressed formats inaccessible.


There is a possibility for sharing knowledge here.


AWS? Google? Azure?
nyu: 1.4 petabytes. Initial time estimate of moving everything was 70 days. Use AWS Snowball: they ship you a physical box. It builds checksums on the way in, they plug it in and offload it, running the checksums again. If you have a lot of data they have a semi called the "snowmobile." DirectConnect for dailies. These products make AWS a clear winner.

Additional resources, added later on Slack:
* Working public "Digital Preservation Criteria" which a number of people in the field have collaborated on https://docs.google.com/document/d/1CEkcWskAbph0gQ4ATK_SWYw-6-8zBxnGFfqZiwtfpEI/edit
* This is a great "quick sum up" of potential cloud storage options and the level (according to AVP) of preservation they meet: https://www.avpreserve.com/cloud-storage-vendor-profiles/
