# Public Key Infrastructure
**Note that most of these notes were taken while reading the book *Understanding PKI: Concepts, Standards, and Deployment Considerations Second Edition* by Carlisle Adams and Steve LLoyd**

## Terminology
* secure sign-on: requires user identification and authentication (usually some form of password or secret)
  * sign-on verification to infrastructure locally on client device before giving user access to remote application
* business drivers: cost savings, interoperability intra-entreprise and inter-enterprise, uniform solution within components of business, possibility of achieving security (as opposed to fragmented, complicated integrations between different security solutions with different parts of the business)
* certification authority: trusted authority by a large proportion of the population the *certify* the key pair to an identity (user) in the population by digitally signing a data structure that contains some representation of the identitiy and a corresponding public key
* certificate repository: robust, scalable online repository system to find the public key for a user
* certificate revocation: the breaking of a binding of a public key to an identity (Could be due to name change due to marriage, discovery of a pribvate key by a hacker, etc.)
* key backup and recovery: implement backup and recovery of private decryption keys in case if user forgetting password, destruction of medium (hard disk crash, a small disk breaks, etc.), or replacement of a medium (operating system is reloaded - effectively overwriting local credentials, or an older computer is traded in for a newer one and the credentials are not transferred before old disk is reformatted)
* automatic key update: automate certificate update with no user intervention by PKI itself by checking the validity period of user certificate when user wants to do something and their user certificate is required, and if expiration date is approaching, a renewal process occurs and a new certificate is generated.This might be necessary due to current knowledge in cryptanalysis with respect to asymmetric algorithms and key lengths, or desire to limit the amount of data encrypted by a particular key.
* key history: maintain record of old keys to be able to access data encrypted with previous keys; PKI needs ti hold onto keys in history, provide backup and recovery as appropriate, and find the appropriate key that corresponds to any protected data
* cross-certification: enable users of one PKI community to validate the certificates of users in another PKI community (in the event of a merger, acquisition, addition of new partners and suppliers, etc.) to avoid having to revoke and issue new certificates by acquiring company
* support for non-repudiation: PKI must provide support for avoiding or preventing repudiation (denial of an action) by providing some of the required technical evidence for a human to use their discretion and judgment in weighing the evidence and providing the final decision since a PKI cannot provide true or full non-repudiation by itself
* time stamping: time source must be trusted and time value must be securely conveyed within PKI
* client software: the PKI provides the sever with all necessary info and tools to support client, but only does so when client makes a request to the server
  * Client software is code that exists outside every application and implements the required client end of the PKI services.
  * Applications *use* the infrastructure; they are not *part of* the infrastructure
  * client software implies nothing about the size of permanence of software, as the software can be:
    * quite large (the "fat client"), performing much of the PKI operational processing such as certificate path processing and validation
    * quite small (the "thin client"), simply calling out to external servers for these PKI functions
    * a Java applet or similar mobile code, downloaded in real time on an as-needed basis and then erased when the calling application (such as a web browser) is shut down
    * a dynamically linked library (DLL), or similar, that resides permanently on the client platform
