# Vivvo DID Specification
##  W3C Editor's Draft 21 September 2018 

**This version:**

[https://github.com/Vivvo/vivvo-did-spec](https://github.com/Vivvo/vivvo-did-spec)

**Latest published version:**

[https://www.w3.org/TR/vivvo-did-scheme/](https://www.w3.org/TR/vivvo-did-scheme/)

**Editors:**

[Jamie Jamieson](https://github.com/jjamieson1)

## About
The Vivvo DID method specification conforms to the requirements specified in the DID specification currently published by the W3C Credentials Community Group. For more information about DIDs and DID method specifications, please see the DID Primer and DID Spec.

## Abstract
Vivvo is a private ledger designed specifically and only for privacy-preserving self-sovereign identity. The Vivvo Ledger is governed by Vivvo Application Studios. As a private ledger designed exclusively for self-sovereign identity, Vivvo is optimized for DIDs and DID Documents. DIDs are created, stored, and used with verifiable claims. This specification covers how these DIDs are managed. It also describes related features of Vivvo of particular interest to DID owners, guardians, and developers.

## Status of This Document
This section describes the status of this document at the time of its publication. Other documents may supersede this document. A list of current W3C publications and the latest revision of this technical report can be found in the W3C technical reports index at https://www.w3.org/TR/.

Publication as an Editor's Draft does not imply endorsement by the W3C Membership. This is a draft document and may be updated, replaced or obsoleted by other documents at any time. It is inappropriate to cite this document as other than work in progress.

This document was produced by a group operating under the W3C Patent Policy. W3C maintains a public list of any patent disclosures made in connection with the deliverables of the group; that page also includes instructions for disclosing a patent. An individual who has actual knowledge of a patent which the individual believes contains Essential Claim(s) must disclose the information in accordance with section 6 of the W3C Patent Policy.

This document is governed by the [1 March 2019 W3C Process Document.](https://www.w3.org/2019/Process-20190301/)
Table of Contents

##  1. Vivvo DID Method

The namestring that shall identify this DID method is: vvo

A DID that uses this method MUST begin with the following prefix: did:vvo. Per the DID specification, this string MUST be in lowercase. The remainder of the DID, after the prefix, is the NSI specified below.
2. Target System(s)

##  2 Target System(s)

This DID method applies to the Vivvo network in all its incarnations.

##  3. Namespace Specific Identifier (NSI)

The Vivvo DID scheme is defined by the following ABNF:

vivvo-did = "did:vvo:idstring" *(":" subnamespace)
idstring = 21*22(char)
subnamespace = ALPHA *(ALPHA / DIGIT / "_" / "-")
char = "1" / "2" / "3" / "4" / "5" / "6" / "7" / "8" / "9" / "A" / "B" / "C"
    / "D" / "E" / "F" / "G" / "H" / "J" / "K" / "L" / "M" / "N" / "P" / "Q"
    / "R" / "S" / "T" / "U" / "V" / "W" / "X" / "Y" / "Z" / "a" / "b" / "c"
    / "d" / "e" / "f" / "g" / "h" / "i" / "j" / "k" / "m" / "n" / "o" / "p"
    / "q" / "r" / "s" / "t" / "u" / "v" / "w" / "x" / "y" / "z"

All Vivvo DIDs are base58 encoded using the Bitcoin/IPFS alphabets of a 16-byte uuid. The encoding uses most alphas and digits, omitting 0OIl to avoid readability problems. This gives an NSI length of either 21 or 22 characters, and it means that DIDs are case-sensitive and may not be case-normalized, even though the prefix is always lower-case.

Optional one or more sub namespaces may be specified to indicate which Vivvo system the DID should reference.

## Namestring Generation Method

The 16-byte uuid underlying a Vivvo DID can be generated in various ways--using standard uuid methods, for example, or by selecting the first 16 bytes of a 256 bit Ed25519 verification key (the public portion of the key pair). In the latter case, there may or may not be an active verification key for the identity owner; that information is only available in the key descriptions in the owner section of the DID Document.

A convenient regex to match *vvo* DIDs is:

``` ^[1-9A-HJ-NP-Za-km-z]{21,22}$ ```

A convenient regex to match the entire did string is:

``` ^did:vvo:[1-9A-HJ-NP-Za-km-z]{21,22}(?<namespace>(?::\w[-\w]*)*)$ ```

## Examples

A valid *vvo* DID might be: *did:vvo:2wJPyULfLLnYTEFYzByfUR.*

↑ 
