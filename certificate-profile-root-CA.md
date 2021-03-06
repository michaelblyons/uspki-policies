## Self-Signed Root CA Certificate Profile


| **Field** |       |       | **Value**                             |
| :-------- | :---: | :---: | :-------------------------------     |
| Version   |       |       | v3 (2)                                 |
| Serial Number   |       |       | Must be a unique positive integer with a minimum of 64 bits (minimum of 8 octets), not to exceed 20 octets  |
| Issuer Signature Algorithm   |       |       |  sha256 WithRSAEncryption {1 2 840 113549 1 1 11}  |
| Issuer Distinguished Name   |       |       |  Unique X.500 Root CA DN as specified in Section 7.1.4 of this CP <br><br>The Root CA DN shall use the format: <br>cn=US Federal TLS Root CA, o=U.S. Government, c=US <br>All non-production Root CA DNs shall include "Test" in the cn. Example: <br>cn=US Federal Test TLS Root CA, o=U.S. Government, c=US <br> <br>Distinguished Name shall conform to PrintableString string type in ASN.1 notation. |
| Validity Period   |       |       |  Encoded as UTCTime for dates through 2049 and GeneralizedTime for dates thereafter <br> No longer than 20 years from date of issue  |
| Subject Distinguished Name   |       |       |   Matches the Issuer DN   |
| Subject Public Key Information   |       |       |   4096 bit modulus, rsaEncryption {1 2 840 113549 1 1 1}   |
| Issuer Signature   |       |       |   sha256 WithRSAEncryption {1 2 840 113549 1 1 11}    |
|               |                 |              |                                       |
| **Extension** |  **Required**   | **Critical** | **Value**                             |
| subjectInfoAccess  | Mandatory | False |  id-ad-caRepository (1.3.6.1.5.5.7.48.5) <br> At least one instance of this access method that includes the URI name form to specify the location of an HTTP accessible location where CA certificates issued by the subject of this certificate may be found. The certificate artifact(s) served by the HTTP accessible location shall be in a BER or DER encoded "certs-only" CMS message as specified in [RFC5752]. This extension is required to assist in monitoring and discovery of, and promote transparency for, the Subordinate CAs signed by the Root. |
| basicConstraints   | Mandatory | True |  cA=True <br> Pathlen is not present |
| Subject Key Identifier   | Mandatory | False |  Octet String <br> Derived using SHA-1 hash of the public key  |
| Key Usage   | Mandatory | True | keyCertSign, crlSign   |  
