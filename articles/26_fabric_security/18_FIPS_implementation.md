# FIPS Overview

FIPS (Federal Information Processing Standards) is a set of standards that defines encryption algorithms and other digital technology processes for use within non-military federal government agencies and by any government contractors working with these agencies. 

In particular, FIPS 140-2 (Federal Information Processing Standard 140-2) is a security accreditation program for validating that the cryptographic modules produced by private sector companies meet well-defined security standards.
[FIPS PUB 140-2](https://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.140-2.pdf) provides the full list of instructions and architecture documents needed to meet the Cryptographic Modules Security requirements.


## Fabric and FIPS

K2View has implemented the [Bouncycastle](https://www.bouncycastle.org/index.html) Java stack for FIPS.
By default, Fabric works in FIPS mode off. Yet, even when FIPS mode is switched off, Fabric only uses FIPS-compliant modules.
Protocols and standards embedded in Fabric encryption algorithm

### FIPS with mode set to **ON**

```fabric>version fips;```

```
|Check                        |Result                                                          |Status|
+-----------------------------+----------------------------------------------------------------+------+
|FIPS Mode                    |on                                                              |passed|
|FIPS Ready                   |140-2                                                           |passed|
|info                         |Bouncy Castle FIPS Java API 1.0.2.1                             |passed|
|info                         |CMVP Certificate #3514                                          |passed|
|HMAC                         |d68017e6f45512a51a862c77e4fa2348d0d24d816bc3f76fcf30375052216e86|passed|
|AES/CBC/PKCS5Padding Explicit|BCFIPS                                                          |passed|
|AES/CBC/PKCS5Padding Implicit|BCFIPS                                                          |passed|
|SHA512_256Secure             |BCFIPS                                                          |passed|
|SHA512Secure                 |BCFIPS                                                          |passed|
|SHA256Secure                 |BCFIPS                                                          |passed|
|SHA512_256                   |BCFIPS                                                          |passed|
|SHA512                       |BCFIPS                                                          |passed|
|SHA256                       |BCFIPS                                                          |passed|
|SHA1                         |BCFIPS                                                          |passed|
|MD5                          |BCFIPS                                                          |passed|
|STRONG_AES256                |BCFIPS                                                          |passed|
|PLAIN_AES256                 |BCFIPS                                                          |passed|
|PLAIN_AES128                 |BCFIPS                                                          |passed|
|SSL Context                  |BCJSSE                                                          |passed|
|SecureRandom                 |BCFIPS                                                          |passed|

 
(20 rows)
```

Note that:
- BCFIPS means that the algorithm is provided via the jar file bc-fips-1.0.1.jar
- BCJSSE means that the Java Secure Socket Extension (JSSE) from Bouncy Castle is used.

### FIPS with mode set to **STRICT**

```fabric>version fips;```

```
|Check                        |Result                                                          |Status|
+-----------------------------+----------------------------------------------------------------+------+
|FIPS Mode                    |strict                                                          |passed|
|FIPS Ready                   |140-2                                                           |passed|
|info                         |Bouncy Castle FIPS Java API 1.0.2.1                             |passed|
|info                         |CMVP Certificate #3514                                          |passed|
|FIPS Only Algorithms         |true                                                            |passed|
|TLS FIPS only mode           |true                                                            |passed|
|HMAC                         |d68017e6f45512a51a862c77e4fa2348d0d24d816bc3f76fcf30375052216e86|passed|
|SunJCE                       |Not present                                                     |passed|
|AES/CBC/PKCS5Padding Explicit|BCFIPS                                                          |passed|
|AES/CBC/PKCS5Padding Implicit|BCFIPS                                                          |passed|
|SHA512_256Secure             |BCFIPS                                                          |passed|
|SHA512Secure                 |BCFIPS                                                          |passed|
|SHA256Secure                 |BCFIPS                                                          |passed|
|SHA512_256                   |BCFIPS                                                          |passed|
|SHA512                       |BCFIPS                                                          |passed|
|SHA256                       |BCFIPS                                                          |passed|
|SHA1                         |BCFIPS                                                          |passed|
|MD5                          |BCFIPS                                                          |passed|
|STRONG_AES256                |BCFIPS                                                          |passed|
|PLAIN_AES256                 |BCFIPS                                                          |passed|
|PLAIN_AES128                 |BCFIPS                                                          |passed|
|SSL Context                  |BCJSSE                                                          |passed|
|SecureRandom                 |BCFIPS                                                          |passed|

(23 rows)
 ```



